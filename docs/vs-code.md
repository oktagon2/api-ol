# VS Code

## Neues Projekt mit GitHub als Versionsverwaltung erstellen
* Im Browser GitHub öffnen und sich anmelden
* Oben rechts aus dem drop-down Menu mit dem Plus-Icon den Eintrag "New repository" wählen
* "Repository name" angeben
* Auf "Create repository" klicken
* Sich die URL, die unter "Quick setup" rechts neben "SSH" angezeigt wird, merken
* VS Code starten
* F1 drücken
* Aus der Liste "Git: Clone" suchen und auswählen
* Als URL die sich oben gemerkte URL eingeben und die Return Taste drücken
* Einen Ordner auswählen 
* Auf "Select Repository Location" klicken. Für das Repository wird dann im ausgewählten Ordner ein neuer Unterordner angelegt.
* Den neuen Ordner öffnen

## Neue Web App erstellen und auf Azure als Static Web App veröffentlichen
* Neues Projekt mit GitHub als Versionsverwaltung erstellen
* Sicherstellen, dass in VS Code die Extension "Azure Static Web Apps" installiert ist
* Generell gemäss [Azure Static Web Apps for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurestaticwebapps) Kapitel "Create your first static web app" vorgehen.

### Einfache statische Webseite
HINWEIS: Diesem Use Case ist die VS Code Azure Extension nicht gewachsen. Beim Erstellen der neuen Azure Static Web App werden nur 5 Fragen gestellt. Gemäss [Azure Static Web Apps for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurestaticwebapps) Kapitel "Create your first static web app" müssten aber 6 Fragen gestellt werden. Deshalb schlägt der Build fehl. Der Build funktioniert erst, wenn man den GitHub Workflow korrigiert hat. Wie das geht steht weiter unten in diesem Kapitel.
* in der Projekt Root wenigstens eine index.html Datei erstellen
* Stagen und commiten
* Azure Extension öffnen
* Im Abschnitt "Static Web Apps" auf das Plus Symbol klicken
* Bei "Enter a name for the new static web app" einen Namen für die Static Web App Ressource in Azure eingeben 
* Bei "Select a location for new resources" "West Europe" auswählen
* Bei "Choose build preset to configure default project structure" "Custom" auswählen
* Bei "Enter the location of your application code" "/" eingeben
* Bei "Enter the location of your build output" allfällige Inhalte löschen und nichts eingeben
* Danach startet der Build. Der Build kann wie folgt überwacht werden:
* Repository in GitHub öffnen und auf Actions klicken.
* Der erste Build wird fehlschlagen. Da das Problem wird im Protokoll mit "[WARNING] Api Directory Location: 'api' could not be found." beschrieben. Der Protokoll Eintrag "Failed to find a default file in the app artifacts folder (/)" ist nicht korrekt und scheint ein Folgefehler zu sein. 
* Um erfolgreich zu builden:
* In Visual Studio im Projekt die yml-Datei aus .github\workflows öffnen.
* Bei api_location und bei output_location "" eintragen.
* Stagen, commiten und pushen. Der Build Prozess startet wieder und diesmal sollte das ganze fehlerfrei enden.
* Azure Extension öffnen
* Im Abschnitt "Static Web Apps" dein Abo aufklappen
* Aus dem Context Menü von der neuen Static Web App den Eintrag "Browse Site" wählen. Deine einfache statische Web Seite wird im Browser angezeigt.
