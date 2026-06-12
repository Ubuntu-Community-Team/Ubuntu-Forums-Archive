---
title: "can't install unity-tweak-tool Depends: unity-webapps-service (&gt;= 2.3.8-0ubuntu3)"
date: 2017-12-11
forum: Installation &amp; Upgrades
---

### Post by giloulounet on 2017-12-11
Hello, im trying to install unity tweak tool but i dont know how to do. can you help me to fix it please. thanks in advance.

```

gilou@gilou:~$ sudo apt-get install unity-tweak-tool
[sudo] password for gilou: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-tweak-tool : Depends: unity-webapps-common but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
gilou@gilou:~$ unity-webapps-common
unity-webapps-common: command not found
gilou@gilouwhoo:~$ sudo apt-get install unity-webapps-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-webapps-common : Depends: unity-webapps-service (>= 2.3.8-0ubuntu3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
gilou@gilou:~$ sudo apt-get install unity-webapps-service
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-webapps-service : Depends: webapp-container
E: Unable to correct problems, you have held broken packages.
gilou@gilou:~$ sudo apt-get install webapp-container
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 webapp-container : Depends: qtbase-abi-5-5-1
                    Depends: qtdeclarative-abi-5-5-0
                    Depends: liboxideqt-qmlplugin (>= 1.8) but it is not going to be installed
                    Depends: qml-module-ubuntu-web (= 0.23+16.04.20161028-0ubuntu2) but it is not going to be installed
                    Depends: qtdeclarative5-ubuntu-ui-toolkit-plugin (>= 1.3) or
                             qtdeclarative5-ubuntu-ui-toolkit-plugin-gles (>= 1.3) but it is not going to be installed
                    Depends: unity-webapps-qml but it is not going to be installed
                    Depends: webbrowser-app (= 0.23+16.04.20161028-0ubuntu2)
E: Unable to correct problems, you have held broken packages.
gilou@gilou:~$ sudo apt-get install qtbase-abi-5-5-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package qtbase-abi-5-5-1 is a virtual package provided by:
  libqt5core5a 5.5.1+dfsg-16ubuntu7.5 [Not candidate version]
  libqt5core5a 5.5.1+dfsg-16ubuntu7 [Not candidate version]


E: Package 'qtbase-abi-5-5-1' has no installation candidate
gilou@gilouwhoo:~$ sudo apt-get install qtbase-abi-5-5-1 -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package qtbase-abi-5-5-1 is a virtual package provided by:
  libqt5core5a 5.5.1+dfsg-16ubuntu7.5 [Not candidate version]
  libqt5core5a 5.5.1+dfsg-16ubuntu7 [Not candidate version]


E: Package 'qtbase-abi-5-5-1' has no installation candidate
gilou@gilou:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gilou@gilou:~$ sudo apt-get install -f qtbase-abi-5-5-1 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package qtbase-abi-5-5-1 is a virtual package provided by:
  libqt5core5a 5.5.1+dfsg-16ubuntu7.5 [Not candidate version]
  libqt5core5a 5.5.1+dfsg-16ubuntu7 [Not candidate version]


E: Package 'qtbase-abi-5-5-1' has no installation candidate

```
????
I dont know what to do ………

---

### Post by Darth4212 on 2017-12-15
Okay open up a terminal and run ```
apt list --installed
```
If the output is too long to post go to [https://pastebin.com/](https://pastebin.com/) and post it there and add a link

---

### Post by deadflowr on 2017-12-15
What version of Ubuntu is in use?
Seems the packages requested do not exist on any currently supported versions of Ubuntu.

---

### Post by Darth4212 on 2017-12-15
> **deadflowr said:**
> What version of Ubuntu is in use?
Seems the packages requested do not exist on any currently supported versions of Ubuntu.
He may be able to get them but in deb packages not too sure though.

---

### Post by deadflowr on 2017-12-15
Found it.
The system is xenial and the OP hasn't done a full system update yet,
or the OP thought they did a full system update but it did not actually do a full system update.

The OP needs to either try running the Software Updater and apply all the updates, or run
```
sudo apt update
sudo apt full-upgrade
```
and post the output if any Errors come up.

Once the system is fully up-to-date, then installing unity-tweak-tool will work.

---

### Post by giloulounet on 2017-12-20
Thank you for your replies,

> **Darth4212 said:**
> Okay open up a terminal and run ```
apt list --installed
```
If the output is too long to post go to [https://pastebin.com/](https://pastebin.com/) and post it there and add a link

done : [https://pastebin.com/KdCBFNQB](https://pastebin.com/KdCBFNQB)


> **deadflowr said:**
> What version of Ubuntu is in use?
Seems the packages requested do not exist on any currently supported versions of Ubuntu.

ubuntu 16.04

> **deadflowr said:**
> Found it.
The system is xenial and the OP hasn't done a full system update yet,
or the OP thought they did a full system update but it did not actually do a full system update.

The OP needs to either try running the Software Updater and apply all the updates, or run
```
sudo apt update
sudo apt full-upgrade
```
and post the output if any Errors come up.

Once the system is fully up-to-date, then installing unity-tweak-tool will work.

done : 

```
gilou@gilou:~$ sudoapt-get update
[sudo] Mot de passede gilou : 
Désolé, essayez denouveau.
[sudo] Mot de passede gilou : 
Atteint:1https://repo.skype.com/deb stable InRelease
Atteint:2https://deb.opera.com/opera-stable stable InRelease
Atteint:3https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease
Réception de:4http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Atteint:5http://archive.canonical.com/ubuntu xenial InRelease                 
Ign:6http://dl.google.com/linux/earth/deb stable InRelease                   
Atteint:7http://be.archive.ubuntu.com/ubuntu xenial InRelease                 
Atteint:8http://dl.google.com/linux/earth/deb stable Release                  
Ign:9http://repo.vivaldi.com/stable/deb stable InRelease                     
Réception de:10http://be.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Atteint:11http://repo.vivaldi.com/stable/deb stable Release                   
Ign:14http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages  
Réception de:15http://be.archive.ubuntu.com/ubuntu xenial-backports InRelease [102kB]
Ign:16https://dl.bintray.com/hawkeye116477/waterfox-deb release InRelease    
Réception de:17http://be.archive.ubuntu.com/ubuntu xenial-updates/main amd64Packages [681 kB]
Réception de:18http://be.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages[639 kB]
Ign:19http://be.archive.ubuntu.com/ubuntu xenial-updates/mainTranslation-en  
Ign:20http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages   
Atteint:21https://dl.bintray.com/hawkeye116477/waterfox-deb release Release   
Ign:23http://be.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11Metadata
Ign:24http://be.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64Icons
Ign:25http://security.ubuntu.com/ubuntu xenial-security/main Translation-en  
Ign:26http://be.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64Packages
Ign:27http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11Metadata
Ign:28http://be.archive.ubuntu.com/ubuntu xenial-updates/restricted i386Packages
Ign:29http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64Icons
Ign:30http://be.archive.ubuntu.com/ubuntu xenial-updates/restrictedTranslation-en
Ign:31http://security.ubuntu.com/ubuntu xenial-security/restricted amd64Packages
Ign:32http://be.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64DEP-11 Metadata
Ign:33http://security.ubuntu.com/ubuntu xenial-security/restricted i386Packages
Ign:34http://be.archive.ubuntu.com/ubuntu xenial-updates/universe amd64Packages
Ign:35http://security.ubuntu.com/ubuntu xenial-security/restrictedTranslation-en
Ign:36http://be.archive.ubuntu.com/ubuntu xenial-updates/universe i386Packages
Ign:37http://be.archive.ubuntu.com/ubuntu xenial-updates/universeTranslation-en
Ign:38http://be.archive.ubuntu.com/ubuntu xenial-updates/universe amd64DEP-11 Metadata
Ign:39http://security.ubuntu.com/ubuntu xenial-security/restricted amd64DEP-11 Metadata
Ign:40http://security.ubuntu.com/ubuntu xenial-security/universe amd64Packages
Ign:41http://be.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-1164x64 Icons
Ign:42http://security.ubuntu.com/ubuntu xenial-security/universe i386Packages
Ign:43http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64Packages
Ign:44http://security.ubuntu.com/ubuntu xenial-security/universeTranslation-en
Ign:45http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386Packages
Ign:46http://security.ubuntu.com/ubuntu xenial-security/universe amd64DEP-11 Metadata
Ign:47http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverseTranslation-en
Ign:48http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64DEP-11 Metadata
Ign:49http://security.ubuntu.com/ubuntu xenial-security/universe DEP-1164x64 Icons
Ign:50http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-1164x64 Icons
Atteint:51http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease   
Ign:52http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64Packages
Ign:53http://be.archive.ubuntu.com/ubuntu xenial-backports/main amd64Packages
Ign:54http://security.ubuntu.com/ubuntu xenial-security/multiverse i386Packages
Ign:55http://be.archive.ubuntu.com/ubuntu xenial-backports/main i386Packages 
Ign:57http://security.ubuntu.com/ubuntu xenial-security/multiverseTranslation-en
Ign:58http://be.archive.ubuntu.com/ubuntu xenial-backports/mainTranslation-en
Ign:59http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64DEP-11 Metadata
Ign:60http://be.archive.ubuntu.com/ubuntu xenial-backports/main amd64DEP-11 Metadata
Ign:61http://security.ubuntu.com/ubuntu xenial-security/multiverse DEP-1164x64 Icons
Ign:62http://be.archive.ubuntu.com/ubuntu xenial-backports/main DEP-1164x64 Icons
Ign:63http://be.archive.ubuntu.com/ubuntu xenial-backports/restricted amd64DEP-11 Metadata
Ign:14http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages  
Atteint:56https://netcologne.dl.sourceforge.net/project/ubuntuzilla/mozilla/aptall InRelease
Ign:64http://be.archive.ubuntu.com/ubuntu xenial-backports/universe amd64Packages
Ign:65http://be.archive.ubuntu.com/ubuntu xenial-backports/universe i386Packages
Ign:20http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages   
Ign:66http://be.archive.ubuntu.com/ubuntu xenial-backports/universeTranslation-en
Ign:25http://security.ubuntu.com/ubuntu xenial-security/main Translation-en  
Ign:27http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11Metadata
Ign:67http://be.archive.ubuntu.com/ubuntu xenial-backports/universe amd64DEP-11 Metadata
Ign:29http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64Icons
Ign:68http://be.archive.ubuntu.com/ubuntu xenial-backports/universe DEP-1164x64 Icons
Ign:31http://security.ubuntu.com/ubuntu xenial-security/restricted amd64Packages
Ign:69http://be.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64DEP-11 Metadata
Ign:70http://be.archive.ubuntu.com/ubuntu xenial-backports/multiverseDEP-11 64x64 Icons
Ign:33http://security.ubuntu.com/ubuntu xenial-security/restricted i386Packages
Ign:35http://security.ubuntu.com/ubuntu xenial-security/restrictedTranslation-en
Ign:39http://security.ubuntu.com/ubuntu xenial-security/restricted amd64DEP-11 Metadata
Ign:40http://security.ubuntu.com/ubuntu xenial-security/universe amd64Packages
Ign:42http://security.ubuntu.com/ubuntu xenial-security/universe i386Packages
Ign:44http://security.ubuntu.com/ubuntu xenial-security/universeTranslation-en
Ign:46http://security.ubuntu.com/ubuntu xenial-security/universe amd64DEP-11 Metadata
Ign:19http://be.archive.ubuntu.com/ubuntu xenial-updates/mainTranslation-en  
Ign:23http://be.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11Metadata
Ign:49http://security.ubuntu.com/ubuntu xenial-security/universe DEP-1164x64 Icons
Ign:24http://be.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64Icons
Ign:52http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64Packages
Ign:26http://be.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64Packages
Ign:54http://security.ubuntu.com/ubuntu xenial-security/multiverse i386Packages
Ign:28http://be.archive.ubuntu.com/ubuntu xenial-updates/restricted i386Packages
Ign:57http://security.ubuntu.com/ubuntu xenial-security/multiverseTranslation-en
Ign:30http://be.archive.ubuntu.com/ubuntu xenial-updates/restrictedTranslation-en
Ign:59http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64DEP-11 Metadata
Ign:32http://be.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64DEP-11 Metadata
Ign:34http://be.archive.ubuntu.com/ubuntu xenial-updates/universe amd64Packages
Ign:61http://security.ubuntu.com/ubuntu xenial-security/multiverse DEP-1164x64 Icons
Ign:36http://be.archive.ubuntu.com/ubuntu xenial-updates/universe i386Packages
Ign:37http://be.archive.ubuntu.com/ubuntu xenial-updates/universeTranslation-en
Ign:38http://be.archive.ubuntu.com/ubuntu xenial-updates/universe amd64DEP-11 Metadata
Réception de:14http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages[519 kB]
Ign:41http://be.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-1164x64 Icons
Ign:43http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64Packages
Ign:45http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386Packages
Ign:47http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverseTranslation-en
Ign:48http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64DEP-11 Metadata
Ign:50http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-1164x64 Icons
Ign:53http://be.archive.ubuntu.com/ubuntu xenial-backports/main amd64Packages
Ign:55http://be.archive.ubuntu.com/ubuntu xenial-backports/main i386Packages 
Ign:58http://be.archive.ubuntu.com/ubuntu xenial-backports/mainTranslation-en
Ign:60http://be.archive.ubuntu.com/ubuntu xenial-backports/main amd64DEP-11 Metadata
Ign:62http://be.archive.ubuntu.com/ubuntu xenial-backports/main DEP-1164x64 Icons
Ign:63http://be.archive.ubuntu.com/ubuntu xenial-backports/restricted amd64DEP-11 Metadata
Ign:64http://be.archive.ubuntu.com/ubuntu xenial-backports/universe amd64Packages
Ign:65http://be.archive.ubuntu.com/ubuntu xenial-backports/universe i386Packages
Ign:66http://be.archive.ubuntu.com/ubuntu xenial-backports/universeTranslation-en
Réception de:20http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages[473 kB]
Ign:67http://be.archive.ubuntu.com/ubuntu xenial-backports/universe amd64DEP-11 Metadata
Ign:68http://be.archive.ubuntu.com/ubuntu xenial-backports/universe DEP-1164x64 Icons
Ign:69http://be.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64DEP-11 Metadata
Ign:70http://be.archive.ubuntu.com/ubuntu xenial-backports/multiverseDEP-11 64x64 Icons
Réception de:19http://be.archive.ubuntu.com/ubuntu xenial-updates/mainTranslation-en [400 kB]
Réception de:23http://be.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11Metadata [483 kB]
Err:24http://be.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64Icons
  Impossibled'ouvrir le fichier/var/lib/apt/lists/partial/be.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_icons-64x64.tar.gz- open (13: Permission non accordée) [IP : 91.189.88.152 80]
Réception de:26http://be.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64Packages [13,7 kB]
Réception de:28http://be.archive.ubuntu.com/ubuntu xenial-updates/restricted i386Packages [13,7 kB]
Réception de:30http://be.archive.ubuntu.com/ubuntu xenial-updates/restrictedTranslation-en [2 754 B]
Ign:32http://be.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64DEP-11 Metadata
Réception de:34http://be.archive.ubuntu.com/ubuntu xenial-updates/universe amd64Packages [725 kB]
Réception de:25http://security.ubuntu.com/ubuntu xenial-security/main Translation-en[251 kB]
Réception de:27http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11Metadata [86,1 kB]
Err:29http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64Icons
  Impossibled'ouvrir le fichier/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_main_dep11_icons-64x64.tar.gz- open (13: Permission non accordée) [IP : 91.189.88.162 80]
Réception de:31http://security.ubuntu.com/ubuntu xenial-security/restricted amd64Packages [12,9 kB]
Réception de:33http://security.ubuntu.com/ubuntu xenial-security/restricted i386Packages [13,0 kB]
Réception de:35http://security.ubuntu.com/ubuntu xenial-security/restrictedTranslation-en [2 479 B]
Ign:39http://security.ubuntu.com/ubuntu xenial-security/restricted amd64DEP-11 Metadata
Réception de:40http://security.ubuntu.com/ubuntu xenial-security/universe amd64Packages [238 kB]
Réception de:36http://be.archive.ubuntu.com/ubuntu xenial-updates/universe i386Packages [680 kB]
Réception de:42http://security.ubuntu.com/ubuntu xenial-security/universe i386Packages [198 kB]
Réception de:44http://security.ubuntu.com/ubuntu xenial-security/universeTranslation-en [128 kB]
Réception de:46http://security.ubuntu.com/ubuntu xenial-security/universe amd64DEP-11 Metadata [63,6 kB]
Ign:49http://security.ubuntu.com/ubuntu xenial-security/universe DEP-1164x64 Icons
Réception de:52http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64Packages [3 481 B]
Réception de:37http://be.archive.ubuntu.com/ubuntu xenial-updates/universeTranslation-en [308 kB]
Réception de:38http://be.archive.ubuntu.com/ubuntu xenial-updates/universe amd64DEP-11 Metadata [254 kB]
Ign:41http://be.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-1164x64 Icons
Réception de:43http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64Packages [18,5 kB]
Réception de:53http://be.archive.ubuntu.com/ubuntu xenial-backports/main amd64Packages [5 174 B]
Réception de:55http://be.archive.ubuntu.com/ubuntu xenial-backports/main i386Packages [5 166 B]
Réception de:58http://be.archive.ubuntu.com/ubuntu xenial-backports/mainTranslation-en [3 234 B]
Réception de:60http://be.archive.ubuntu.com/ubuntu xenial-backports/main amd64DEP-11 Metadata [3 487 B]
Err:62http://be.archive.ubuntu.com/ubuntu xenial-backports/main DEP-1164x64 Icons
  Impossibled'ouvrir le fichier/var/lib/apt/lists/partial/be.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_icons-64x64.tar.gz- open (13: Permission non accordée) [IP : 91.189.88.149 80]
Ign:63http://be.archive.ubuntu.com/ubuntu xenial-backports/restricted amd64DEP-11 Metadata
Réception de:64http://be.archive.ubuntu.com/ubuntu xenial-backports/universe amd64Packages [7 146 B]
Réception de:65http://be.archive.ubuntu.com/ubuntu xenial-backports/universe i386Packages [7 149 B]
Réception de:66http://be.archive.ubuntu.com/ubuntu xenial-backports/universeTranslation-en [3 812 B]
Réception de:67http://be.archive.ubuntu.com/ubuntu xenial-backports/universe amd64DEP-11 Metadata [4 957 B]
Ign:68http://be.archive.ubuntu.com/ubuntu xenial-backports/universe DEP-1164x64 Icons
Atteint:69http://be.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64DEP-11 Metadata
Ign:70http://be.archive.ubuntu.com/ubuntu xenial-backports/multiverseDEP-11 64x64 Icons
3 239 koréceptionnés en 20s (158 ko/s)                                       
Lecture des listesde paquets... Fait
W:https://download.01.org/gfx/ubuntu/16.04/main/dists/xenial/InRelease:Signature by key 09D6EF97BFB38E916EF060E756A3DEF863961D39 uses weakdigest algorithm (SHA1)
E: Impossible derécupérerhttp://security.ubuntu.com/ubuntu/dists/xenial-security/main/dep11/icons-64x64.tar Impossible d'ouvrir le fichier/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_main_dep11_icons-64x64.tar.gz- open (13: Permission non accordée) [IP : 91.189.88.162 80]
E: Impossible derécupérerhttp://be.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dep11/icons-64x64.tar Impossible d'ouvrir le fichier/var/lib/apt/lists/partial/be.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_icons-64x64.tar.gz- open (13: Permission non accordée) [IP : 91.189.88.152 80]
E: Impossible derécupérerhttp://be.archive.ubuntu.com/ubuntu/dists/xenial-backports/main/dep11/icons-64x64.tar Impossible d'ouvrir le fichier/var/lib/apt/lists/partial/be.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_icons-64x64.tar.gz- open (13: Permission non accordée) [IP : 91.189.88.149 80]
E: Le téléchargementde quelques fichiers d'index a échoué, ils ont été ignorés, oules anciens ont été utilisés à la place.
gilou@gilou:~$ sudoapt-get full-upgrade
Lecture des listesde paquets... Fait
Construction del'arbre des dépendances       
Lecture desinformations d'état... Fait
Calcul de la mise àjour... Fait
Les paquets suivantsseront mis à jour :
  libarchive13liblmdb0
2 mis à jour, 0nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessairede prendre 326 ko dans les archives.
Après cetteopération, 59,4 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vouscontinuer ? [O/n] o
ATTENTION : lespaquets suivants n'ont pas été authentifiés.
  libarchive13liblmdb0
Faut-il installerces paquets sans vérification ? [o/N] n
E: Certains paquetsn'ont pas pu être authentifiés
gilou@gilou:~$  
```


 
Thank you for your help. 
Hope you will help me to find a solution,
Cordially,
Gilou

---

### Post by giloulounet on 2017-12-20
I can repost the result of the [FONT=Ubuntu Mono, monospace][COLOR=#000000]sudo apt full update in english if necessary. 
it is in french... [/COLOR][/FONT]

---

### Post by deadflowr on 2017-12-21
Indeed a problem with apt failing.
You need to try to clear the partial directory
Try this
```
sudo -i
rm /var/lib/apt/lists/partial/*
exit
```
then re-run apt-get update command again and see if those errors are gone or not.

Referenced from here:
[https://askubuntu.com/questions/917603/sudo-apt-get-update-failing-could-not-open-list-file-due-to-permission-deni]("https://askubuntu.com/questions/917603/sudo-apt-get-update-failing-could-not-open-list-file-due-to-permission-deni")

Indeed type carefully and double check the rm command's path before hitting enter.

If no more errors show, then you need to run the upgrade commands:
```
sudo apt full-upgrade
```

You do have a warning about the intel repository using a weak key for it's repo, but that shouldn't be a problem for now.
Basically it's telling you that the key is weaker than what apt uses (currently apt moved to sha256)
it's possible that after an update it'll be fixed.

Hope it helps

---

### Post by giloulounet on 2017-12-21
Thank's for your help deadflowr, 
I have still this problem when i do an update : 
```
W: https://download.01.org/gfx/ubuntu/16.04/main/dists/xenial/InRelease: Signature by key 09D6EF97BFB38E916EF060E756A3DEF863961D39 uses weak digest algorithm (SHA1)

```

I'm dont know what it means.

and, unfortunately, I still can't install unity-tweak-tool…

```
sudo apt-get install unity-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-tweak-tool : Depends: unity-webapps-common but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

---

### Post by deadflowr on 2017-12-21
Did you run the full-upgrade command I posted?

---

### Post by giloulounet on 2017-12-21
> **deadflowr said:**
> Did you run the full-upgrade command I posted?
Yes, i did.

---

### Post by deadflowr on 2017-12-21
What was the output of the full-upgrade command?

---

### Post by giloulounet on 2017-12-21
> **deadflowr said:**
> What was the output of the full-upgrade command?
```
sudo apt-get full-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

---

### Post by deadflowr on 2017-12-21
A couple of things to do,
first, what does the command
```
sudo apt-get install -f
```
do? 
(please post the output)
and second, what does
```
apt-cache policy unity-webapps-common
```
show?

If we're lucky the first will resolve any issues the second might have shown.

---

### Post by giloulounet on 2017-12-21
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

AND

unity-webapps-common:
  Installed: (none)
  Candidate: 2.4.17+15.10.20150616-0ubuntu2
  Version table:
     2.4.17+15.10.20150616-0ubuntu2 500
        500 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        500 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) xenial/main i386 Packages

---

### Post by Darth4212 on 2017-12-21
Try installing unity-webapps-common by downloading it from here: [https://packages.ubuntu.com/xenial/all/unity-webapps-common/download](https://packages.ubuntu.com/xenial/all/unity-webapps-common/download)  then open a terminal and run ```
cd ~/Downloads/
``` then run ```
sudo dpkg -i unity-webapps-common_2.4.17+15.10.20150616-0ubuntu2_all.deb
``` then try installing unity-tweak-tool.

If you get any errors post them.

---

### Post by giloulounet on 2017-12-21
sudo dpkg -i unity-webapps-common_2.4.17+15.10.20150616-0ubuntu2_all.deb
(Reading database ... 346954 files and directories currently installed.)
Preparing to unpack unity-webapps-common_2.4.17+15.10.20150616-0ubuntu2_all.deb ...
Unpacking unity-webapps-common (2.4.17+15.10.20150616-0ubuntu2) over (2.4.17+15.10.20150616-0ubuntu2) ...
dpkg: dependency problems prevent configuration of unity-webapps-common:
 unity-webapps-common depends on unity-webapps-service (>= 2.3.8-0ubuntu3); however:
  Package unity-webapps-service is not installed.


dpkg: error processing package unity-webapps-common (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 unity-webapps-common

---

### Post by giloulounet on 2017-12-21
I solve the problem after doing this : [https://pastebin.com/uvbj313e](https://pastebin.com/uvbj313e)

Thank you very much for your help. 

I'm so gratefull. 
:)

So, now, unity-tweak-tool is working. 

VERY BIG BIG BIG THANK'S

---

### Post by giloulounet on 2017-12-21
Love ubuntu debian linux community

---

