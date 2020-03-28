# Visual Studio Code per OS161
## Configurazione

 1. Installare visual studio code tramite il link: 
	[https://code.visualstudio.com/docs/setup/linux#_debian-and-ubuntu-based-distributions](https://code.visualstudio.com/docs/setup/linux#_debian-and-ubuntu-based-distributions)
 2. Installare il pacchetto C/C++
![enter image description here](https://code.visualstudio.com/assets/docs/cpp/cpp/cpp-extension.png)
 3. Scaricare le configurazioni dal git:
	[https://github.com/thomascristofaro/os161vscode](https://github.com/thomascristofaro/os161vscode)
 4. Estrai la cartella “.vscode” dentro la cartella: `home/pds/os161/os161-base-2.0.2/kern`
	 - Se non la vedi premi `CTRL+H` perché è una cartella nascosta
 5. Ora apri Visual studio code, apri la cartella `home/pds/os161/os161-base-2.0.2/kern` e dovresti avere un’interfaccia senza errori (di include, intellisense…) e pronto per le modifiche

## Utilizzo
### Task definite:

 - **Copy Config**: copia il file di configurazione DUMBVM nella nuova versione che poi configureremo con Run Config
	`cp conf/DUMBVM conf/${input:VersionName}` 
 - **Run Config**: Fa partire il processo di configurazione della nuova versione
	`cd conf/;./config ${input:VersionName}`
 - **Make Depend**: Inserisce le dipendenze nella cartella di installazione
	`cd compile/${input:VersionName};bmake depend`
 - **Build and Install**: Compila la nuova versione e sposta l'eseguile nella cartella del run
	`cd compile/${input:VersionName};bmake;bmake install`
 - **Run OS161**: Fa partire il sistema all'interno del terminale di VS Code
`cd /home/pds/pds-os161/root;sys161 -w kernel`


### Come si utilizzano

 - **Build and Install** è definita come task di default, quindi si può richiamare tramite la combinazione `CTRL+SHIFT+B`
 - Le altre si possono richiamare tramite la Command Palette `CTRL+SHIFT+P` > Run Task > seleziona task > scrivi versione
   - È possibile assegnare una combinazione di tasti alla chiamata Run Task: Preferences > Keyboard Shortcuts
   - Riferimento: [https://code.visualstudio.com/docs/getstarted/keybindings](https://code.visualstudio.com/docs/getstarted/keybindings)

### Debugger

Per entrare in debug bisogna premere F5 (o tramite run nella finestra debug) e bisogna aver attivato sys161 in modalità debug. Vi consiglio di utilizzare il task **Run OS161** prima di attivare il debug in modo da avere il sistema OS161 nel terminale di VS Code e avere tutto in un solo ambiente.
Riferimento debug VS Code: 
 - [https://code.visualstudio.com/docs/editor/debugging](https://code.visualstudio.com/docs/editor/debugging), 
- [https://code.visualstudio.com/docs/cpp/cpp-debug](https://code.visualstudio.com/docs/cpp/cpp-debug)


### Ogni miglioria ai file di configurazione è ben accetta
