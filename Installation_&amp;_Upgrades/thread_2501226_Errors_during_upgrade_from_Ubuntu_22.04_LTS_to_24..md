---
title: "Errors during upgrade from Ubuntu 22.04 LTS to 24.04.1 LTS"
date: 2024-09-28
forum: Installation &amp; Upgrades
---

### Post by ubntuuser on 2024-09-28
I got an error concerning Thunderbird update. Later there was a message that the upgrade was stopped and finally a message that the upgrade was finished completely but that there have been errors. I try to add the printscreens of the messages, but I am not sure that it works - so I add the messages here, too (sorry, but they are in German):
Message 1:
"/tmp/apt-dpkg-install-NuOqNW/03-thunderbird_2%3a1snap1-0ubuntu3_amd64.deb" konnte nicht installiert werden"
Die Systemaktualisierung wird fortgesetzt, aber das Paket "/tmp/apt-dpkg-install-NuOqNW/03-thunderbird_2%3a1snap1-0ubuntu3_amd64.deb" könnte sich in einem nicht funktionsfähigen Zustand befinden. Bitte ziehen Sie in Betracht, diesen Fehler zu melden.
"neues thunderbird-Skript des Paketes pre-installation"-Unterprozess gab den Fehlerwert 1 zurück

Message 2:
Die Aktualisierungen konnten nicht installiert werden
Die Systemaktualisierung wurde abgebrochen. Ihr System könnte sich in einem nicht verwendbaren Zustand befinden. Eine Wiederherstellung wird gestartet ("dpkg --configure -a").

Message 3:
Systemaktualisierung wurde abgeschlossen
Die Systemaktualisierung wurde vollständig abgeschlossen, jedoch traten während der Systemaktualisierung Fehler auf.

What I did afterwards:
I rebooted the system. Afterwards I used the following commands:
                       [LEFT] sudo apt-get check => it found [COLOR=#c9211e]t[/COLOR]hunderbird-locale-de

 sudo apt --fix-broken install

 sudo apt autoremove => to delete the packages not longer needed

It seemes that the thunderbird (snap) installation went OK - even if Thunderbird after boot today wanted me to configure a first email account, starting again Thunderbird everything seems to be OK.

Then:

 sudo apt autoremove => there was a warning:
                       
 Warning: The unit file, source configuration file or drop-ins of systemd-binfmt.[/LEFT]
 [LEFT] service changed on disk. Run 'systemctl daemon-reload' to reload units.[/LEFT]
  
so I did: 
[LEFT] systemctl daemon-reload

During the actions some folder are not deleted because they haven't been empty - I have to have a special look...:

 dpkg: Warnung: Altes Verzeichnis »/etc/thunderbird« kann nicht gelöscht werden: 
[/LEFT]
 [LEFT] Das Verzeichnis ist nicht leer[/LEFT]
 [LEFT] dpkg: Warnung: Altes Verzeichnis »/etc/apport/native-origins.d« kann nicht gelös[/LEFT]
 [LEFT] cht werden: Das Verzeichnis ist nicht leer[/LEFT]
 [LEFT] dpkg: Warnung: Altes Verzeichnis »/etc/apport/blacklist.d« kann nicht gelöscht w[/LEFT]
 [LEFT] erden: Das Verzeichnis ist nicht leer[/LEFT]
  [LEFT] dpkg: Warnung: Während Entfernens von fonts-lato ist Verzeichnis »/usr/share/fon[/LEFT]
 [LEFT] ts/truetype/lato« nicht leer, wird daher nicht gelöscht[/LEFT]
    [LEFT][COLOR=#c9211e]
Big question: Is there something left to do to finish the upgrade?

[/COLOR]
[/LEFT]
  [LEFT]

[/LEFT]
 [LEFT]

[/LEFT]
  [LEFT]

[/LEFT]

---

### Post by ubfan1 on 2024-09-28
Translation from the Firefox translate button:
I got an error concerning Thunderbird update. Later was a message that  the upgrade was stopped and finally a message that the upgrade was  finished completely but that there have been been errors. I try to add  the printscreens of the messages, but I am not sure that it works - so I  add the messages here, too (sorry, but they are in German):
Message 1:
"/tmp/apt-dpkg-install-NuOqNW/03-thunderbird-2%3a1snap1-0ubuntu3-amd64.deb" could not be installed"
The  system update continues, but the package  "/tmp/apt-dpkg-install-NuOqNW/03-thunderbird-2%3a1snap1-0ubuntu3-amd64.deb"  may be in a non-functional state. Please consider reporting this error.
"New thunderbird script of the pre-installation underprocess package returned the error value 1

Message 2:
The updates could not be installed
The system update was canceled. Your system may be in unsuitable condition. A recovery is started ("dpkg --configure -a").

Message 3:
System update has been completed
The system update was completely completed, but errors occurred during the system update.

What I did afterwards:
I rebooted the system. Afterwards I used the following commands:
                       [LEFT]sudo apt-get check > it found [COLOR=#c9211e]t[/COLOR]hunder's locale-de   

sudo apt --fix-broken install   

sudo apt autoremove > to delete the packages not longer neededed  

It seemes that the thunderbird (snap) installation went OK -  even if Thunderbird after boot today wanted me to configure a first  email account, starting again Thunderbird everything seems to be OK.  

Then:   

sudo apt autoremove > there was a warning:                          

Warning: The unit file, source configuration file or drop-ins of systemd-binfmt.
[/LEFT]
 [LEFT]service changed on disk. Run 'systemctl daemon-reload' to reload units.
[/LEFT]
  
so I did:
[LEFT]systemctl daemon-reload  

During the actions some folder are not deleted because the haven't been empty - I have to have a special look...:   

dpkg: Warning: Old directory »/etc/thunderbird» cannot be deleted: 
[/LEFT]
 [LEFT]The directory is not empty
[/LEFT]
 [LEFT]dpkg: Warning: Old directory »/etc/apport/native-origins.d. cannot be solved[/LEFT]
 [LEFT]The directory is not empty[/LEFT]
 [LEFT]dpkg: Warning: Old directory »/etc/apport/blacklist.d» cannot be deleted w[/LEFT]
 [LEFT]probe: The directory is not empty[/LEFT]
  [LEFT]dpkg: Warning: During removing fonts-lato is a directory »/usr/share/fon[/LEFT]
 [LEFT]ts/truetype/lato not empty, therefore not deleted
[/LEFT]
     [COLOR=#c9211e]
Big question: Is there something to left to do to finish the upgrade?  [/COLOR]

---

