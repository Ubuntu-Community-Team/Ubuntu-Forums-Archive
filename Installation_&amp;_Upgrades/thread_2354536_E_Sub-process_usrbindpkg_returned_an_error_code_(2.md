---
title: "E: Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2017-03-03
forum: Installation &amp; Upgrades
---

### Post by ledisciple on 2017-03-03
Hello everybody

I try this

```
sudo apt-get update
sudo apt-get upgrade

```

but

```
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

I try these without succes

```
sudo dpkg --configure -a
```
```
sudo dpkg --configure -a
sudo apt-get install xdg-utils
```

Can you help me please?

Thanks

---

### Post by deadflowr on 2017-03-03
Post the full output of the update/upgrade commands, please.

---

### Post by ledisciple on 2017-03-03
It's in French

```
sudo apt-get update
```

The return :
```
Atteint:1 http://archive.canonical.com/ubuntu yakkety InRelease
Atteint:2 http://archive.ubuntu.com/ubuntu yakkety InRelease                   
Réception de:3 http://archive.ubuntu.com/ubuntu yakkety-updates InRelease [102 kB]
Ign:4 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety InRelease              
Atteint:5 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu yakkety InRelease
Réception de:6 http://security.ubuntu.com/ubuntu yakkety-security InRelease [102 kB]
Ign:7 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety Release                
Ign:8 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Sources           
Ign:9 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all Packages      
Atteint:10 http://download.virtualbox.org/virtualbox/debian yakkety InRelease  
Ign:11 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 Packages    
Ign:12 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr
Ign:13 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr_FR
Ign:14 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-en
Ign:15 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all DEP-11 Metadata
Ign:17 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main DEP-11 64x64 Icons
Ign:8 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Sources
Ign:9 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all Packages
Ign:11 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 Packages
Ign:12 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr
Ign:13 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr_FR
Ign:14 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-en
Ign:15 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all DEP-11 Metadata
Ign:17 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main DEP-11 64x64 Icons
Ign:8 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Sources
Ign:9 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all Packages
Ign:11 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 Packages
Ign:12 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr
Ign:13 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr_FR
Atteint:18 https://deb.opera.com/opera-stable stable InRelease
Ign:14 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-en
Ign:15 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all DEP-11 Metadata
Ign:17 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main DEP-11 64x64 Icons
Ign:8 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Sources
Ign:9 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all Packages
Ign:11 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 Packages
Ign:12 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr
Ign:13 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr_FR
Réception de:19 http://archive.ubuntu.com/ubuntu yakkety-updates/universe i386 Packages [129 kB]
Ign:14 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-en   
Ign:15 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all DEP-11 Metadata
Ign:17 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main DEP-11 64x64 Icons
Ign:8 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Sources
Ign:9 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all Packages      
Réception de:20 http://archive.ubuntu.com/ubuntu yakkety-updates/universe i386 DEP-11 Metadata [102 kB]
Ign:11 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 Packages    
Réception de:21 http://security.ubuntu.com/ubuntu yakkety-security/universe i386 DEP-11 Metadata [9 740 B]
Réception de:22 http://archive.ubuntu.com/ubuntu yakkety-updates/universe DEP-11 64x64 Icons [134 kB]
Ign:12 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr   
Réception de:23 http://security.ubuntu.com/ubuntu yakkety-security/main i386 DEP-11 Metadata [8 272 B]
Réception de:24 http://security.ubuntu.com/ubuntu yakkety-security/main DEP-11 64x64 Icons [10,0 kB]
Ign:13 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr_FR
Réception de:25 http://archive.ubuntu.com/ubuntu yakkety-updates/main i386 Packages [197 kB]
Ign:14 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-en   
Ign:15 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all DEP-11 Metadata
Réception de:26 http://archive.ubuntu.com/ubuntu yakkety-updates/main i386 DEP-11 Metadata [147 kB]
Ign:17 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main DEP-11 64x64 Icons
Réception de:27 http://archive.ubuntu.com/ubuntu yakkety-updates/main DEP-11 64x64 Icons [81,3 kB]
Err:8 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Sources           
  404  Not Found
Ign:9 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all Packages 
Ign:11 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 Packages
Ign:12 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr
Ign:13 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-fr_FR
Ign:14 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main Translation-en
Ign:15 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main i386 DEP-11 Metadata
Ign:16 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main all DEP-11 Metadata
Ign:17 http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety/main DEP-11 64x64 Icons
1 023 ko réceptionnés en 5s (171 ko/s)
Lecture des listes de paquets... Fait
W: The repository 'http://ppa.launchpad.net/crebs/ppa/ubuntu yakkety Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:42
E: Impossible de récupérer http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/yakkety/main/source/Sources  404  Not Found
E: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list:42

```

```
sudo apt-get upgrade
``` 

return 

```
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Calcul de la mise à jour... Fait
Les paquets suivants seront mis à jour :
  chromium-codecs-ffmpeg-extra fonts-wine gnome-calculator
  libapache2-mod-php7.0 libegl1-mesa libgbm1 libgd3 libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libnm-glib-vpn1 libnm-glib4 libnm-gtk-common
  libnm-gtk0 libnm-util2 libnm0 libnma-common libnma0 libnss-resolve
  libosmesa6 libpam-systemd libsystemd0 libtiff5 libudev1 libwayland-egl1-mesa
  libwine libwine-development libxatracker2 mesa-va-drivers mesa-vdpau-drivers
  network-manager network-manager-gnome opera-stable php7.0 php7.0-bz2
  php7.0-cli php7.0-common php7.0-gd php7.0-json php7.0-mbstring php7.0-mcrypt
  php7.0-mysql php7.0-opcache php7.0-readline php7.0-xml php7.0-zip
  snap-confine snapd systemd systemd-sysv ubuntu-core-launcher udev
  wine-development wine-stable wine32 wine32-development
56 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 7 481 ko/119 Mo dans les archives.
Après cette opération, 2 286 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer ? [O/n] o
Réception de:1 http://archive.ubuntu.com/ubuntu yakkety-updates/main i386 snapd i386 2.22.6+16.10 [7 081 kB]
Réception de:2 http://security.ubuntu.com/ubuntu yakkety-security/universe i386 php7.0-zip i386 7.0.15-0ubuntu0.16.10.4 [21,4 kB]
Réception de:3 http://security.ubuntu.com/ubuntu yakkety-security/universe i386 php7.0-mcrypt i386 7.0.15-0ubuntu0.16.10.4 [14,8 kB]
Réception de:4 http://archive.ubuntu.com/ubuntu yakkety-updates/main i386 network-manager-gnome i386 1.2.6-0ubuntu1 [313 kB]
Réception de:5 http://archive.ubuntu.com/ubuntu yakkety-updates/universe i386 wine-development all 1.9.20-1ubuntu2 [51,0 kB]
7 445 ko réceptionnés en 42s (174 ko/s)                                        
Extraction des modèles depuis les paquets : 53%E: Erreur de lecture - read (5: Erreur d'entrée/sortie)
E: Erreur interne, ne peut localiser la partie control.tar.{lz4gzxzbz2lzma}
E: Prior errors apply to /var/cache/apt/archives/wine32-development_1.9.20-1ubuntu2_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libwine-development_1.9.20-1ubuntu2_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libxatracker2_12.0.6-0ubuntu0.16.10.1_i386.deb
E: Prior errors apply to /var/cache/apt/archives/mesa-va-drivers_12.0.6-0ubuntu0.16.10.1_i386.deb
E: Prior errors apply to /var/cache/apt/archives/mesa-vdpau-drivers_12.0.6-0ubuntu0.16.10.1_i386.deb
E: Prior errors apply to /var/cache/apt/archives/php7.0_7.0.15-0ubuntu0.16.10.4_all.deb
debconf: Échec d'apt-extracttemplates : No such file or directory
Extraction des modèles depuis les paquets : 100%
Préconfiguration des paquets...
dpkg: avertissement: le fichier contenant la liste des fichiers du paquet « linux-generic » étant manquant, il est considéré qu'aucun fichier du paquet n'est actuellement installé
dpkg: avertissement: le fichier contenant la liste des fichiers du paquet « ogmrip » étant manquant, il est considéré qu'aucun fichier du paquet n'est actuellement installé
dpkg: avertissement: le fichier contenant la liste des fichiers du paquet « linux-image-generic » étant manquant, il est considéré qu'aucun fichier du paquet n'est actuellement installé
dpkg: unrecoverable fatal error, aborting:
 lecture de la liste des fichiers du paquet « ogmrip-doc »: Erreur d'entrée/sortie
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by deadflowr on 2017-03-03
Try a cleanup, as it looks like a corruption in the archives in your cache.
```
sudo apt-get clean
```
this will clear out the cache.

Then try re-rerunning the update/upgrade commands.

---

