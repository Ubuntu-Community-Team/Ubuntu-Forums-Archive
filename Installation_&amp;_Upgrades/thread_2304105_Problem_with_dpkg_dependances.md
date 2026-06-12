---
title: "Problem with dpkg dependances"
date: 2015-11-24
forum: Installation &amp; Upgrades
---

### Post by Urs_Helfenstein on 2015-11-24
Hi, 

Since a while I have some issues that the system ask to update some stuff, but then it ends with an error. So I thought to update the version 14.04 to 15.04 and tried to use "sudo apt-get dist-upgrade". This command ends with the following error:

```

E: Unerfüllte Abhängigkeiten. Versuchen Sie, -f zu benutzen.
```
This means translated somthing like that there are too much dependencies and one should try to use option -f

So I tried to run:

```
sudo apt-get -f install
```

But also this command ends with the following error:

```

dpkg: parse error, in file '/var/lib/dpkg/status' near line 162 package 'python-pkg-resources':
 Feld »Depends«, ungültiger Paketname »python:any«: Zeichen »:« nicht erlaubt (nur Buchstaben, Ziffern und die Zeichen »-+._«)
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

It seems that there is an error with the package 'python-pkg-resources'. 

How can I solve this issue?

Thank you for any support. 
BR, 
Urs

---

### Post by TheFu on 2015-11-24
Upgrades from 14.04 directly to 15.04 are not possible.
The path is 14.04 --> 14.10 (Support ended last June) --> 15.04 (support ends in 1 month) -->15.10 (Support ends in June)

My machines are on 14.04 LTS awaiting June 2016 to be updated to 16.04, which is the next LTS.  Most of the 14.04 servers are running production services and will not move to a new release until 18.04.  LTS-->LTS-->LTS **is** a supported release upgrade path.

So, I would restore the backup made just prior to the first attempted updates ... and simply remain patched on 14.04 for the next 5-7 months by using:
```
sudo aptitude update
sudo aptitude upgrade
```
on a weekly basis.

BTW, it is absolutely critical to have a fully patched system before attempting any release-to-release migration. Was that the case?

Make sense?

---

### Post by Urs_Helfenstein on 2015-11-24
Hi, 

Thank you for reply and your advices. The system I running is was already upgraded in the past from a 13.xx version (do not know exactly which version it was). But so far it runs without any issues. But about one month ago there were some issues with dependencies. 

aptitude is not installed so far. I tried it with:

```

 sudo apt-get install aptitude
```

But also here the following appears:

```
dem@dem-EasyNote-TK81:~$ sudo apt-get install aptitude
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Probieren Sie »apt-get -f install«, um dies zu korrigieren:
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 aptitude : Hängt ab von: aptitude-common (= 0.6.11-1ubuntu3) soll aber nicht installiert werden
            Hängt ab von: libboost-iostreams1.55.0 soll aber nicht installiert werden
            Hängt ab von: libcwidget3 soll aber nicht installiert werden
            Empfiehlt: aptitude-doc-en soll aber nicht installiert werden oder
                       aptitude-doc
 bash-completion : Hängt ab von (vorher): dpkg (>= 1.15.7.2~) soll aber nicht installiert werden
 chromium-codecs-ffmpeg-extra : Hängt ab von (vorher): dpkg (>= 1.15.6) soll aber nicht installiert werden
 cmake : Hängt ab von (vorher): dpkg (>= 1.17.5~) soll aber nicht installiert werden
 cron : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 cups : Hängt ab von: cups-core-drivers (>= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 soll installiert werden
        Hängt ab von: cups-daemon (>= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 soll installiert werden
        Hängt ab von: cups-client (>= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 soll installiert werden
 cups-bsd : Hängt ab von: cups-client (= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 soll installiert werden
 cups-client : Hängt ab von: libcups2 (= 1.7.2-0ubuntu1.6) aber 2.0.2-1ubuntu3 soll installiert werden
 cups-core-drivers : Hängt ab von: libcups2 (= 1.7.2-0ubuntu1.6) aber 2.0.2-1ubuntu3 soll installiert werden
 cups-daemon : Hängt ab von: libcups2 (= 1.7.2-0ubuntu1.6) aber 2.0.2-1ubuntu3 soll installiert werden
               Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 dash : Hängt ab von: dpkg (>= 1.15.0) soll aber nicht installiert werden
 fontconfig : Hängt ab von (vorher): dpkg (>= 1.16.1) soll aber nicht installiert werden
 fonts-droid : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 fonts-kacst : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 fonts-kacst-one : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 fonts-nanum : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 fonts-sil-abyssinica : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 fonts-takao-pgothic : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 imagemagick-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 install-info : Hängt ab von (vorher): dpkg (>= 1.16.1) soll aber nicht installiert werden
 language-pack-de : Hängt ab von (vorher): dpkg (>= 1.16.1) soll aber nicht installiert werden
 language-pack-de-base : Hängt ab von (vorher): dpkg (>= 1.16.1) soll aber nicht installiert werden
 language-pack-en : Hängt ab von (vorher): dpkg (>= 1.16.1) soll aber nicht installiert werden
 language-pack-en-base : Hängt ab von (vorher): dpkg (>= 1.16.1) soll aber nicht installiert werden
 language-pack-gnome-de : Hängt ab von (vorher): dpkg (>= 1.16.1) soll aber nicht installiert werden
 language-pack-gnome-de-base : Hängt ab von (vorher): dpkg (>= 1.16.1) soll aber nicht installiert werden
 language-pack-gnome-en : Hängt ab von (vorher): dpkg (>= 1.16.1) soll aber nicht installiert werden
 language-pack-gnome-en-base : Hängt ab von (vorher): dpkg (>= 1.16.1) soll aber nicht installiert werden
 language-selector-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 libav-tools : Hängt ab von (vorher): dpkg (>= 1.15.7.2~) soll aber nicht installiert werden
 libcommon-sense-perl : Hängt ab von: perl (>= 5.20.2~) aber 5.18.2-2ubuntu1 soll installiert werden
                        Hängt ab von: perlapi-5.20.2
 libdpkg-perl : Hängt ab von: dpkg (>= 1.15.8) soll aber nicht installiert werden
 libmtp9 : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 libqt5core5a : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5dbus5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5gui5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5multimedia5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5network5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5opengl5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5printsupport5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5qml-graphicaleffects : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5sql5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5sql5-sqlite : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5svg5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5test5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5webkit5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5webkit5-qmlwebkitplugin : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5widgets5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libqt5xml5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libquvi7 : Hängt ab von (vorher): dpkg (>= 1.15.6) soll aber nicht installiert werden
 libreoffice-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2~) soll aber nicht installiert werden
 libsmbclient : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 libunity-gtk2-parser0 : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 libunity-gtk3-parser0 : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 libwbclient0 : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 lightdm : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 linux-image-3.13.0-37-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-40-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-43-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-44-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-45-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-46-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-48-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-49-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-51-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-52-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-53-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-54-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-55-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-57-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-63-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.13.0-65-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.5.0-42-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 linux-image-3.8.0-35-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) soll aber nicht installiert werden
 man-db : Hängt ab von (vorher): dpkg (>= 1.16.1~) soll aber nicht installiert werden
 module-init-tools : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 mountall : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 ntpdate : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 openssh-client : Hängt ab von: dpkg (>= 1.7.0) soll aber nicht installiert werden
 pcmciautils : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 perl-base : Hängt ab von (vorher): dpkg (>= 1.14.20) soll aber nicht installiert werden
 poppler-data : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 popularity-contest : Hängt ab von: dpkg (>= 1.10) soll aber nicht installiert werden
 python-minimal : Hängt ab von: dpkg (>= 1.13.20) soll aber nicht installiert werden
 python-support : Hängt ab von: dpkg (>= 1.14.19) soll aber nicht installiert werden
 python3-minimal : Hängt ab von: dpkg (>= 1.13.20) soll aber nicht installiert werden
 qtdeclarative5-ubuntu-ui-toolkit-plugin : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 samba-common : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 sgml-base : Hängt ab von (vorher): dpkg (>= 1.16.4) soll aber nicht installiert werden
 smbclient : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 ubuntu-drivers-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 ubuntu-sso-client : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 ubuntu-ui-toolkit-theme : Hängt ab von (vorher): dpkg (>= 1.15.6~) soll aber nicht installiert werden
 unity-gtk2-module : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 unity-gtk3-module : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 update-notifier-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
 zeitgeist-core : Hängt ab von (vorher): dpkg (>= 1.15.7.2) soll aber nicht installiert werden
E: Unerfüllte Abhängigkeiten. Versuchen Sie »apt-get -f install« ohne Angabe eines Pakets (oder geben Sie eine Lösung an).
```


May be a problem with corrupting packages. How can I remove them or solve this issue with another measure?

Thanks!
Urs

---

### Post by grahammechanical on 2015-11-24
Some people like to use Aptitude but we can use apt-get. So, lets us not get distracted trying to install Aptitude. Please run

```
sudo apt-get update
sudo apt-get upgrade
```

What errors do you get? Do you still see dependency problems? and does

```
sudo apt-get -f install
```

not fix the problem? As a matter of interest, what did you do to upgrade from 14.04 to 15.04? Did you run a command? What was it?

Regards.

---

### Post by Urs_Helfenstein on 2015-11-24
Okay. 

The output of apt-get update is:

```

...
...
...
Holen: 24 http://ch.archive.ubuntu.com trusty-backports/multiverse Translation-en [1'215 B]                                                                    
Holen: 25 http://ch.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]                                                                       
Holen: 26 http://ch.archive.ubuntu.com trusty-backports/universe Translation-en [33.9 kB]                                                                      
OK   http://ch.archive.ubuntu.com trusty Release                                                                                                               
OK   http://ch.archive.ubuntu.com trusty/main Sources                                                                                                          
OK   http://ch.archive.ubuntu.com trusty/restricted Sources                                                                                                    
OK   http://ch.archive.ubuntu.com trusty/universe Sources                                                                                                      
OK   http://ch.archive.ubuntu.com trusty/multiverse Sources                                                                                                    
OK   http://ch.archive.ubuntu.com trusty/main amd64 Packages                                                                                                   
OK   http://ch.archive.ubuntu.com trusty/restricted amd64 Packages                                                                                             
OK   http://ch.archive.ubuntu.com trusty/universe amd64 Packages                                                                                               
OK   http://ch.archive.ubuntu.com trusty/multiverse amd64 Packages                                                                                             
OK   http://ch.archive.ubuntu.com trusty/main Translation-de                                                                                                   
OK   http://ch.archive.ubuntu.com trusty/main Translation-en                                                                                                   
OK   http://ch.archive.ubuntu.com trusty/multiverse Translation-de                                                                                             
OK   http://ch.archive.ubuntu.com trusty/multiverse Translation-en                                                                                             
OK   http://ch.archive.ubuntu.com trusty/restricted Translation-de                                                                                             
OK   http://ch.archive.ubuntu.com trusty/restricted Translation-en                                                                                             
OK   http://ch.archive.ubuntu.com trusty/universe Translation-de                                                                                               
OK   http://ch.archive.ubuntu.com trusty/universe Translation-en                                                                                               
Ign http://ch.archive.ubuntu.com trusty/main Translation-de_CH                                                                                                 
Ign http://ch.archive.ubuntu.com trusty/multiverse Translation-de_CH                                                                                           
Ign http://ch.archive.ubuntu.com trusty/restricted Translation-de_CH                                                                                           
Ign http://ch.archive.ubuntu.com trusty/universe Translation-de_CH                                                                                             
Es wurden 2'110 kB in 27 s geholt (77.1 kB/s).                                                                                                                 
W: Fehlschlag beim Holen von http://ppa.launchpad.net/freefilesync/ffs/ubuntu/dists/vivid/main/binary-amd64/Packages  404  Not Found

E: Einige Indexdateien konnten nicht heruntergeladen werden. Sie wurden ignoriert oder alte an ihrer Stelle benutzt.

```

The output of apt-get upgrade is:

```

dem@dem-EasyNote-TK81:~$ sudo apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Probieren Sie »apt-get -f install«, um dies zu korrigieren.
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 bash-completion : Hängt ab von (vorher): dpkg (>= 1.15.7.2~) ist aber nicht installiert
 chromium-codecs-ffmpeg-extra : Hängt ab von (vorher): dpkg (>= 1.15.6) ist aber nicht installiert
 cmake : Hängt ab von (vorher): dpkg (>= 1.17.5~) ist aber nicht installiert
 cron : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 cups : Hängt ab von: cups-core-drivers (>= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 ist installiert
        Hängt ab von: cups-daemon (>= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 ist installiert
        Hängt ab von: cups-client (>= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 ist installiert
 cups-bsd : Hängt ab von: cups-client (= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 ist installiert
 cups-client : Hängt ab von: libcups2 (= 1.7.2-0ubuntu1.6) aber 2.0.2-1ubuntu3 ist installiert
 cups-core-drivers : Hängt ab von: libcups2 (= 1.7.2-0ubuntu1.6) aber 2.0.2-1ubuntu3 ist installiert
 cups-daemon : Hängt ab von: libcups2 (= 1.7.2-0ubuntu1.6) aber 2.0.2-1ubuntu3 ist installiert
               Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 dash : Hängt ab von: dpkg (>= 1.15.0) ist aber nicht installiert
 fontconfig : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 fonts-droid : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 fonts-kacst : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 fonts-kacst-one : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 fonts-nanum : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 fonts-sil-abyssinica : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 fonts-takao-pgothic : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 imagemagick-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 install-info : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-de : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-de-base : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-en : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-en-base : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-gnome-de : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-gnome-de-base : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-gnome-en : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-gnome-en-base : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-selector-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 libav-tools : Hängt ab von (vorher): dpkg (>= 1.15.7.2~) ist aber nicht installiert
 libcommon-sense-perl : Hängt ab von: perl (>= 5.20.2~) aber 5.18.2-2ubuntu1 ist installiert
                        Hängt ab von: perlapi-5.20.2
 libdpkg-perl : Hängt ab von: dpkg (>= 1.15.8) ist aber nicht installiert
 libmtp9 : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 libqt5core5a : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5dbus5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5gui5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5multimedia5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5network5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5opengl5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5printsupport5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5qml-graphicaleffects : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5sql5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5sql5-sqlite : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5svg5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5test5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5webkit5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5webkit5-qmlwebkitplugin : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5widgets5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5xml5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libquvi7 : Hängt ab von (vorher): dpkg (>= 1.15.6) ist aber nicht installiert
 libreoffice-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2~) ist aber nicht installiert
 libsmbclient : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libunity-gtk2-parser0 : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 libunity-gtk3-parser0 : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 libwbclient0 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 lightdm : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 linux-image-3.13.0-37-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-40-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-43-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-44-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-45-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-46-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-48-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-49-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-51-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-52-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-53-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-54-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-55-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-57-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-63-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-65-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.5.0-42-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.8.0-35-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 man-db : Hängt ab von (vorher): dpkg (>= 1.16.1~) ist aber nicht installiert
 module-init-tools : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 mountall : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 ntpdate : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 openssh-client : Hängt ab von: dpkg (>= 1.7.0) ist aber nicht installiert
 pcmciautils : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 perl-base : Hängt ab von (vorher): dpkg (>= 1.14.20) ist aber nicht installiert
 poppler-data : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 popularity-contest : Hängt ab von: dpkg (>= 1.10) ist aber nicht installiert
 python-minimal : Hängt ab von: dpkg (>= 1.13.20) ist aber nicht installiert
 python-support : Hängt ab von: dpkg (>= 1.14.19) ist aber nicht installiert
 python3-minimal : Hängt ab von: dpkg (>= 1.13.20) ist aber nicht installiert
 qtdeclarative5-ubuntu-ui-toolkit-plugin : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 samba-common : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 sgml-base : Hängt ab von (vorher): dpkg (>= 1.16.4) ist aber nicht installiert
 smbclient : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 ubuntu-drivers-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 ubuntu-sso-client : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 ubuntu-ui-toolkit-theme : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 unity-gtk2-module : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 unity-gtk3-module : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 update-notifier-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 zeitgeist-core : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
E: Unerfüllte Abhängigkeiten. Versuchen Sie, -f zu benutzen.

```

The outoput of is:

```

sudo apt-get -f install
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Abhängigkeiten werden korrigiert ... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  libbit-vector-perl libcarp-clan-perl libcdr-0.0-0 libclass-data-inheritable-perl libclass-method-modifiers-perl libcmis-0.4-4 libcommon-sense-perl
  libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl libdate-calc-perl libelfg0 libextutils-depends-perl libextutils-pkgconfig-perl libfile-which-perl
  libgoocanvas-common libgoocanvas3 libgtkimageview0 libhttp-server-simple-perl libidl-common libimage-magick-perl libimage-magick-q16-perl libjson-perl
  libjson-xs-perl libmagickcore-6.q16-2 libmouse-perl libmspub-0.0-0 libnet-oauth-perl liborcus-0.6-0 libpath-class-perl libproc-simple-perl libqt5sensors5
  libsort-naturally-perl libthumbnailer0 libtie-ixhash-perl libunique-1.0-0 libvisio-0.0-0 libwww-mechanize-perl libx11-protocol-perl libxml-twig-perl
  libxml-xpathengine-perl perlmagick qt4-default
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden zusätzlichen Pakete werden installiert:
  appmenu-qt5 cups-client cups-core-drivers cups-daemon dpkg init-system-helpers libabw-0.1-1 libalgorithm-c3-perl libalgorithm-diff-xs-perl libapparmor-perl
  libapt-pkg-perl libbit-vector-perl libboost-date-time1.55.0 libboost-iostreams1.55.0 libboost-system1.55.0 libcdr-0.1-1 libcgi-fast-perl libcgi-pm-perl
  libclass-c3-perl libclass-c3-xs-perl libclone-perl libcmis-0.5-5 libcpan-meta-perl libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl
  libdata-optlist-perl libdata-section-perl libdouble-conversion1 libe-book-0.1-1 libeot0 libfcgi-perl libfile-fcntllock-perl libfreehand-0.1-1
  libhtml-parser-perl libimage-magick-perl libimage-magick-q16-perl libio-pty-perl libjson-xs-perl libldb1 liblist-moreutils-perl liblocale-gettext-perl
  libmagickcore-6.q16-2 libmodule-build-perl libmodule-signature-perl libmouse-perl libmro-compat-perl libmspub-0.1-1 libmtp-runtime libmtp9 libmwaw-0.3-3
  libnet-dns-perl libnet-ssleay-perl libodfgen-0.1-1 libpackage-constants-perl libparams-util-perl libperl5.20 libperlio-gzip-perl libplymouth4
  libpod-readme-perl libpurple0 libqt5core5a libqt5dbus5 libqt5gui5 libqt5multimedia5 libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5
  libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5webkit5 libqt5widgets5
  libqt5xml5 libregexp-common-perl libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-style-human libreoffice-style-tango libreoffice-writer librevenge-0.0-0 libsmbclient
  libsnmp30 libsocket6-perl libsoftware-license-perl libsub-exporter-perl libsub-identify-perl libsub-install-perl libsub-name-perl libtext-charwidth-perl
  libtext-iconv-perl libtext-soundex-perl libtext-template-perl libuuid-perl libvisio-0.1-1 libwpd-0.10-10 libwpg-0.3-3 libwps-0.3-3 libxml-libxml-perl
  libxml-parser-perl lsb-base perl perl-base perl-modules perlmagick plymouth plymouth-label python-ldb python-samba python3-uno qml-module-qtgraphicaleffects
  qml-module-qtquick-layouts qml-module-qtquick-localstorage qml-module-qtquick-window2 qml-module-qtquick2 qtdeclarative5-localstorage-plugin
  qtdeclarative5-qtquick2-plugin qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-window-plugin qttranslations5-l10n rename samba-common
  samba-common-bin samba-libs smbclient suru-icon-theme ubuntu-mobile-icons uno-libs3 upstart ure ureadahead
Vorgeschlagene Pakete:
  xpp cups-pdf libdata-dump-perl imagemagick-doc libmagickcore-6.q16-2-extra libreoffice-base libreoffice-style-breeze libreoffice-style-crystal
  libreoffice-style-hicontrast libreoffice-style-oxygen libreoffice-style-sifr libreoffice-evolution crystalcursors kde-icons-crystal tango-icon-theme
  fonts-crosextra-caladea fonts-crosextra-carlito libreoffice-gcj libreoffice-java-common perl-doc libterm-readline-gnu-perl libterm-readline-perl-perl
  libb-lint-perl libcpanplus-dist-build-perl libcpanplus-perl libfile-checktree-perl liblog-message-perl libobject-accessor-perl heimdal-clients graphviz
  upstart-monitor
Die folgenden Pakete werden ENTFERNT:
  grace libcairo-perl libdata-random-perl libdate-calc-xs-perl libgd-perl libglib-perl libgnome2-canvas-perl libgnome2-gconf-perl libgnome2-perl
  libgnome2-vfs-perl libgnome2-wnck-perl libgoo-canvas-perl libgtk2-appindicator-perl libgtk2-imageview-perl libgtk2-perl libgtk2-unique-perl libnet-dbus-perl
  libnet-dropbox-api-perl liboxideqt-qmlplugin liboxideqtquick0 libpango-perl libperl5.18 libproc-processtable-perl libqt5webkit5-qmlwebkitplugin
  libunity-webapps0 qtdeclarative5-dialogs-plugin qtdeclarative5-privatewidgets-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin shutter
  unity-webapps-common unity-webapps-qml unity-webapps-service unity-webapps-youtube webapp-container webbrowser-app xul-ext-unity
  xul-ext-websites-integration
Die folgenden NEUEN Pakete werden installiert:
  dpkg libabw-0.1-1 libalgorithm-c3-perl libboost-date-time1.55.0 libboost-iostreams1.55.0 libboost-system1.55.0 libcdr-0.1-1 libcgi-fast-perl libcgi-pm-perl
  libclass-c3-perl libclass-c3-xs-perl libcmis-0.5-5 libcpan-meta-perl libdata-optlist-perl libdata-section-perl libdouble-conversion1 libe-book-0.1-1 libeot0
  libfcgi-perl libfreehand-0.1-1 libimage-magick-perl libimage-magick-q16-perl libmagickcore-6.q16-2 libmodule-build-perl libmodule-signature-perl
  libmro-compat-perl libmspub-0.1-1 libmwaw-0.3-3 libodfgen-0.1-1 libpackage-constants-perl libparams-util-perl libperl5.20 libplymouth4 libpod-readme-perl
  libregexp-common-perl librevenge-0.0-0 libsoftware-license-perl libsub-exporter-perl libsub-install-perl libtext-template-perl libvisio-0.1-1 libwpd-0.10-10
  libwpg-0.3-3 libwps-0.3-3 qml-module-qtgraphicaleffects qml-module-qtquick-layouts qml-module-qtquick-localstorage qml-module-qtquick-window2
  qml-module-qtquick2 qttranslations5-l10n rename suru-icon-theme ubuntu-mobile-icons
Die folgenden Pakete werden aktualisiert (Upgrade):
  appmenu-qt5 cups-client cups-core-drivers cups-daemon init-system-helpers libalgorithm-diff-xs-perl libapparmor-perl libapt-pkg-perl libbit-vector-perl
  libclone-perl libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl libfile-fcntllock-perl libhtml-parser-perl libio-pty-perl libjson-xs-perl libldb1
  liblist-moreutils-perl liblocale-gettext-perl libmouse-perl libmtp-runtime libmtp9 libnet-dns-perl libnet-ssleay-perl libperlio-gzip-perl libpurple0
  libqt5core5a libqt5dbus5 libqt5gui5 libqt5multimedia5 libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5 libqt5printsupport5
  libqt5qml-graphicaleffects libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5webkit5 libqt5widgets5 libqt5xml5
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-math libreoffice-style-human libreoffice-style-tango libreoffice-writer libsmbclient libsnmp30 libsocket6-perl libsub-identify-perl
  libsub-name-perl libtext-charwidth-perl libtext-iconv-perl libtext-soundex-perl libuuid-perl libxml-libxml-perl libxml-parser-perl lsb-base perl perl-base
  perl-modules perlmagick plymouth plymouth-label python-ldb python-samba python3-uno qtdeclarative5-localstorage-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-window-plugin samba-common samba-common-bin samba-libs smbclient uno-libs3 upstart ure ureadahead
90 aktualisiert, 53 neu installiert, 37 zu entfernen und 428 nicht aktualisiert.
10 nicht vollständig installiert oder entfernt.
Es müssen noch 0 B von 145 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 70.7 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] j
Extrahiere Vorlagen aus Paketen: 100%
Vorkonfiguration der Pakete ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 162 package 'python-pkg-resources':
 Feld »Depends«, ungültiger Paketname »python:any«: Zeichen »:« nicht erlaubt (nur Buchstaben, Ziffern und die Zeichen »-+._«)
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Therefore, each command stops with an error.

Currently I have 14.04 installed but with the issue that since about a month it will not update the system. Therefore, I tried to update the distribution with:

```
sudo apt-get dist-upgrade
```

---

### Post by TheFu on 2015-11-24
dist-upgrade does not upgrade between releases.

You've got to get **apt-get upgrade** fixed before changing to any newer release is possible.

grahammechanical is correct about aptitude.  It does what apt-get does most of time, but when there are complex dependency issues, it can be smarter.

Generally, where the first error is seen is what needs to be fixed before moving onto the next command.
Are there **any** errors with the "update"?  If so, fix those first before moving on to "update".

If any .deb files were manually installed, those packages could be preventing any dependent packages from being updated. Remove them. External PPAs can cause a similar issue and may need to be cleaned up.  Any changes to the list of repos requires re-running **apt-get update** again. That also applies if it has been more than a few hours since the last time it was run.

Really, it would be easier to restore from the backup made just before this was all started. Can you do that?

---

### Post by Urs_Helfenstein on 2015-11-24
I think we came closer. I add some external PPAs. Is there a command to remove them? Or how can I clean them up?

No it is not possible to restore from a backup before it was made. And to setup a new system is also a very bad option because it will need days to create a similar installation (self compiled simulation software). Therefore, I will try to fix that issue.

---

### Post by TheFu on 2015-11-24
Don't feel bad. I learned this stuff the hard way just like you. Got a system so broken that there wasn't any way to fix it except to wipe and start over. Don't think you are there yet and there is still some hope to fix it. Hopefully, once this is fixed, backups will become an automatic, daily, task. [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/)

PPAs are placed in /etc/apt/sources.list.d/ just rename the file so it doesn't end in ".list"
Then run "apt-get update" again followed by upgrade.

BTW, making a backup sufficient to move to a fresh install isn't that hard. There are dpkg commands to make it  relatively pain-free; at least from the package reinstallation parts.  Data still needs to be backed up in the normal way.
Not all packages are available from release-to-release but 95%+ are.

Custom compiled code probably can just be copied over, unless it is tightly dependent on some other installed packages. If there are network libraries, it is important to re-link every few months to get any security patches.

* rename PPA files
* sudo apt-get update
* sudo apt-get upgrade
see where that leaves the system with errors.

---

### Post by Urs_Helfenstein on 2015-11-24
"sudo apt-get update" output:

```

...
...
OK   http://ch.archive.ubuntu.com trusty/universe Translation-en                                                                                               
Ign http://ch.archive.ubuntu.com trusty/main Translation-de_CH                                                                                                 
Ign http://ch.archive.ubuntu.com trusty/multiverse Translation-de_CH                                                                                           
Ign http://ch.archive.ubuntu.com trusty/restricted Translation-de_CH                                                                                           
Ign http://ch.archive.ubuntu.com trusty/universe Translation-de_CH                                                                                             
Es wurden 2'565 kB in 28 s geholt (89.4 kB/s).                                                                                                                 
Paketlisten werden gelesen... Fertig
N: Datei »ubuntu-x-swat-x-updates-quantal.list.distUpgrade2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »ubuntu-x-swat-x-updates-quantal.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »openfoam.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »freefilesync-ubuntu-ffs-vivid.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »openfoam.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-boot-repair-saucy.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-ubuntu-boot-repair-vivid.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-boot-repair-saucy.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-ubuntu-boot-repair-vivid.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »ubuntu-x-swat-x-updates-quantal.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
dem@dem-EasyNote-TK81:~$ 


```


"sudo apt-get upgrade" output:
```

Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Probieren Sie »apt-get -f install«, um dies zu korrigieren.
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 bash-completion : Hängt ab von (vorher): dpkg (>= 1.15.7.2~) ist aber nicht installiert
 chromium-codecs-ffmpeg-extra : Hängt ab von (vorher): dpkg (>= 1.15.6) ist aber nicht installiert
 cmake : Hängt ab von (vorher): dpkg (>= 1.17.5~) ist aber nicht installiert
 cron : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 cups : Hängt ab von: cups-core-drivers (>= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 ist installiert
        Hängt ab von: cups-daemon (>= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 ist installiert
        Hängt ab von: cups-client (>= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 ist installiert
 cups-bsd : Hängt ab von: cups-client (= 2.0.2-1ubuntu3) aber 1.7.2-0ubuntu1.6 ist installiert
 cups-client : Hängt ab von: libcups2 (= 1.7.2-0ubuntu1.6) aber 2.0.2-1ubuntu3 ist installiert
 cups-core-drivers : Hängt ab von: libcups2 (= 1.7.2-0ubuntu1.6) aber 2.0.2-1ubuntu3 ist installiert
 cups-daemon : Hängt ab von: libcups2 (= 1.7.2-0ubuntu1.6) aber 2.0.2-1ubuntu3 ist installiert
               Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 dash : Hängt ab von: dpkg (>= 1.15.0) ist aber nicht installiert
 fontconfig : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 fonts-droid : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 fonts-kacst : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 fonts-kacst-one : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 fonts-nanum : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 fonts-sil-abyssinica : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 fonts-takao-pgothic : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 imagemagick-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 install-info : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-de : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-de-base : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-en : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-en-base : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-gnome-de : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-gnome-de-base : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-gnome-en : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-pack-gnome-en-base : Hängt ab von (vorher): dpkg (>= 1.16.1) ist aber nicht installiert
 language-selector-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 libav-tools : Hängt ab von (vorher): dpkg (>= 1.15.7.2~) ist aber nicht installiert
 libcommon-sense-perl : Hängt ab von: perl (>= 5.20.2~) aber 5.18.2-2ubuntu1 ist installiert
                        Hängt ab von: perlapi-5.20.2
 libdpkg-perl : Hängt ab von: dpkg (>= 1.15.8) ist aber nicht installiert
 libmtp9 : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 libqt5core5a : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5dbus5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5gui5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5multimedia5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5network5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5opengl5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5printsupport5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5qml-graphicaleffects : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5sql5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5sql5-sqlite : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5svg5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5test5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5webkit5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5webkit5-qmlwebkitplugin : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5widgets5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libqt5xml5 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libquvi7 : Hängt ab von (vorher): dpkg (>= 1.15.6) ist aber nicht installiert
 libreoffice-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2~) ist aber nicht installiert
 libsmbclient : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 libunity-gtk2-parser0 : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 libunity-gtk3-parser0 : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 libwbclient0 : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 lightdm : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 linux-image-3.13.0-37-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-40-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-43-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-44-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-45-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-46-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-48-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-49-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-51-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-52-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-53-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-54-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-55-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-57-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-63-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.13.0-65-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.5.0-42-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 linux-image-3.8.0-35-generic : Hängt ab von (vorher): dpkg (>= 1.10.24) ist aber nicht installiert
 man-db : Hängt ab von (vorher): dpkg (>= 1.16.1~) ist aber nicht installiert
 module-init-tools : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 mountall : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 ntpdate : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 openssh-client : Hängt ab von: dpkg (>= 1.7.0) ist aber nicht installiert
 pcmciautils : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 perl-base : Hängt ab von (vorher): dpkg (>= 1.14.20) ist aber nicht installiert
 poppler-data : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 popularity-contest : Hängt ab von: dpkg (>= 1.10) ist aber nicht installiert
 python-minimal : Hängt ab von: dpkg (>= 1.13.20) ist aber nicht installiert
 python-support : Hängt ab von: dpkg (>= 1.14.19) ist aber nicht installiert
 python3-minimal : Hängt ab von: dpkg (>= 1.13.20) ist aber nicht installiert
 qtdeclarative5-ubuntu-ui-toolkit-plugin : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 samba-common : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 sgml-base : Hängt ab von (vorher): dpkg (>= 1.16.4) ist aber nicht installiert
 smbclient : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 ubuntu-drivers-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 ubuntu-sso-client : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 ubuntu-ui-toolkit-theme : Hängt ab von (vorher): dpkg (>= 1.15.6~) ist aber nicht installiert
 unity-gtk2-module : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 unity-gtk3-module : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 update-notifier-common : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
 zeitgeist-core : Hängt ab von (vorher): dpkg (>= 1.15.7.2) ist aber nicht installiert
N: Datei »ubuntu-x-swat-x-updates-quantal.list.distUpgrade2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »ubuntu-x-swat-x-updates-quantal.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »openfoam.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »freefilesync-ubuntu-ffs-vivid.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »openfoam.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-boot-repair-saucy.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-ubuntu-boot-repair-vivid.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-boot-repair-saucy.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-ubuntu-boot-repair-vivid.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »ubuntu-x-swat-x-updates-quantal.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »ubuntu-x-swat-x-updates-quantal.list.distUpgrade2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »ubuntu-x-swat-x-updates-quantal.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »openfoam.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »freefilesync-ubuntu-ffs-vivid.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »openfoam.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-boot-repair-saucy.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-ubuntu-boot-repair-vivid.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-boot-repair-saucy.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »yannubuntu-ubuntu-boot-repair-vivid.list2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
N: Datei »ubuntu-x-swat-x-updates-quantal.list.save2« in Verzeichnis »/etc/apt/sources.list.d/« wird ignoriert, da sie eine ungültige Dateinamen-Erweiterung hat.
E: Unerfüllte Abhängigkeiten. Versuchen Sie, -f zu benutzen.

```


In the apt-get update output I do not see an error. There is just a notice that some files are ignored because of a name which is not valid (because I renamed it to *.list2)

But apt-get upgrade seems to show the same error about non consistent dependencies. 

May be to setup a new system is not that big if you know how to do it ;)
But first I would like to try to repair it... Thank you for your support.

---

### Post by TheFu on 2015-11-24
Is there a LUG nearby?
Used google-translate - doesn't look good. There are packages mixed from different releases. Very bad.
Did you happen to manually change any release names in /etc/apt?

---

### Post by Urs_Helfenstein on 2015-11-24
What is a LUG (sorry, I am not a Ubuntu expert yet ;-))

If you tell me how, I will change the language of the outputs.

No, I never did something manually in the /etc/apt so far.

---

### Post by TheFu on 2015-11-24
[https://en.wikipedia.org/wiki/Linux_user_group](https://en.wikipedia.org/wiki/Linux_user_group) if you don't understand a term, use a web search tool and add "linux" or "ubuntu" to the term.

Try "ubuntu lug" in your search engine of choice. Definitely get comfortable doing searches. The learning path to expert is steep.

BTW, I'm not an Ubuntu expert either. Only been using it since 2008 or so. Before that I used almost every other distro but started with SLS.
[http://blog.jdpfu.com/search/?q=learning+linux](http://blog.jdpfu.com/search/?q=learning+linux)

---

### Post by Urs_Helfenstein on 2015-11-25
The hint with the LUG is interesting. I will see if there is something like this organized near by to learn more. 

But for now: Any idea to solve the package dependency issue?

---

### Post by ian-weisser on 2015-11-25
> **Urs_Helfenstein said:**
>                                                                                                               
W: Fehlschlag beim Holen von [http://ppa.launchpad.net/freefilesync/ffs/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/freefilesync/ffs/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found


1) Delete the PPA from your sources.
2) Uninstall all software from that PPA. **sudo apt-get remove package1 package2 packageN**
3) Autoremove all orphaned dependencies that you received from that PPA. **sudo apt-get autoremove**
4) Clean all the PPA packages out of your local package cache. Or clean out all cached packages with** sudo apt-get clean**
5) Rebuild apt's package database to reflect the new sources (without the PPA). **sudo apt-get update**
6) Test the repair with a normal[B] sudo apt-get upgrade
[/B]

---

### Post by Urs_Helfenstein on 2015-11-25
Hi ian-weisser, 

I deleted all the PPA sources from **/etc/apt/sources.list.d**

I did not ran the **sudo apt-get remove ...** because I did not know which packages are involved.

I ran **sudo apt-get autoremove**, **sudo apt-get clean, **and** [B]sudo apt-get update** [/B]without and issues.

**sudo apt-get upgrade **ends with the following error:

```

...
...
Es wurden 173 MB in 4 min 44 s geholt (607 kB/s).                                                     
Extrahiere Vorlagen aus Paketen: 100%
Vorkonfiguration der Pakete ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 162 package 'python-pkg-resources':
 Feld »Depends«, ungültiger Paketname »python:any«: Zeichen »:« nicht erlaubt (nur Buchstaben, Ziffern und die Zeichen »-+._«)
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I run **head -162 /var/lib/dpkg/status | tail** to get more information about the position mentioned in the error message and got the following:

```

Status: install ok installed
Priority: optional
Section: python
Installed-Size: 273
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: python-setuptools
Version: 12.2-1
Provides: python2.7-setuptools
Depends: python:any (>= 2.7), python:any (<< 2.8)

```

I do not see any error in this parse. I also try to replace the status files with older backups but with the same result... even when I take very old status files there seems to be the same issue. So my assumption is that there is somthin wrong mit dpkg that it identifies valid parses as error. 
How to solve this?

---

### Post by ian-weisser on 2015-11-25
> **Urs_Helfenstein said:**
> I did not ran the **sudo apt-get remove ...** because I did not know which packages are involved.
Then you did not fix the conflict, and your system is probably still broken.
Are you saying that you don't know why you added that PPA? Or all those Vivid packages?

> **Urs_Helfenstein said:**
> I ran **sudo apt-get autoremove**, **sudo apt-get clean, **and** [B]sudo apt-get update** [/B]without and issues.
Expected behavior. Subsequent steps are pointless without removing the top-level conflicting packages first.
However, if you don't know what you added...then you are rather stuck.
If you feel stuck, and you simply want a working system as quickly as possible, backing up your data and reinstalling takes about an hour.

> **Urs_Helfenstein said:**
> I do not see any error in this parse.
Ther error message is unusual, but explicit. It does not seem a bug to me.
Look carefully. The described error on the Depends line is indeed there (":any") twice.
Seems like a rather simple typo to fix...or to unfix if later needed.
That is a Vivid package, and you should be removing it anyway.

---

### Post by Urs_Helfenstein on 2015-11-26
> Then you did not fix the conflict, and your system is probably still broken.
Are you saying that you don't know why you added that PPA? Or all those Vivid packages?

Sorry, may be I was not clear enough. I know why I add the PPAs (e.g.  OpenFoam for CFD simulation / one PPA to install BootRepairDisk / one  PPA to install FreeFileSync ...). What I do not know is which packages I  need to list to remove them. Is there a way to find all the packages  depending to a PPA?

>                     [QUOTE] [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **Urs_Helfenstein**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13396665#post13396665")                 

                 I ran **sudo apt-get autoremove**, **sudo apt-get clean, **and** [B]sudo apt-get update** [/B]without and issues.
                            
Expected behavior. Subsequent steps are pointless without removing the top-level conflicting packages first.
However, if you don't know what you added...then you are rather stuck.
If you feel stuck, and you simply want a working system as quickly as  possible, backing up your data and reinstalling takes about an hour.[/QUOTE]

There was a typo. I meant "without **any** issues".

> Ther error message is unusual, but explicit. It does not seem a bug to me.
Look carefully. The described error on the Depends line is indeed there (":any") twice.
Seems like a rather simple typo to fix...or to unfix if later needed.
That is a Vivid package, and you should be removing it anyway.

I tried to delete this block but there are 138 other ":any" in this status file and even when I look to backup files before this problem there is the same syntax used with ":any". So I still think that this may be a problem with dpkg

You said the Vivid packages should be removed. What is Vivid and how can I remove them?

Thanks for your support!

---

### Post by ian-weisser on 2015-11-26
> **Urs_Helfenstein said:**
> Sorry, may be I was not clear enough. I know why I add the PPAs (e.g.  OpenFoam for CFD simulation / one PPA to install BootRepairDisk / one  PPA to install FreeFileSync ...). What I do not know is which packages I  need to list to remove them. Is there a way to find all the packages  depending to a PPA?

All you need to know is the top-level package you wanted: freefoam or openfoam or whatever it was.
Apt's autoremove will usually do all the rest for you, automatically removing all the openfoam dependencies.

There is a way for the user to determine all the packages from a specific source, but it's tedious (using the apt-cache command for each package). It's also not neccessary - apt already has tools (like autoremove) that do all that tedium for you. Indeed, eliminating that tedium is the entire purpose of Apt!

> **Urs_Helfenstein said:**
> I still think that this may be a problem with dpkg
You are, of course, free to file a bug against dpkg. You are also free to scan the source code, locate the bug, and patch it.
I have not seen this particular issue before,and it may indeed be a bug. Or it may be a simple, expected incompatibility between your 14.04 (Trusty) version of dpkg and your 15.04 (Vivid) package standards.

The inability for dpkg to read the package database changes my recommended solution.
We won't get far trying to uninstall the non-Ubuntu-14.04 software if dpkg cannot use the package database.
My recommended solution is, unfortunately, to back up your data and reinstall. I see no way to repair your system without a large investment of time manually editing those database files.

Lesson: Be careful about your choices of non-Ubuntu and off-version software sources. These aren't phone Apps, with limited access on top of a safe base system. Debian packages are powerful: They are installed by root, and can do *anything* to your system. Choosing the wrong package or version can have unexpected consequences. Preventing such inadvertent damage is one of the design goals of Ubuntu Snappy, currently under development.

---

### Post by TheFu on 2015-11-26
I would have reinstalled a few days ago.

Going too long between updates is both a security issue and a compatibility issue. Staying on an LTS release and updating within about 6 months of each LTS release will mean better help as well.  Can't really suggest non-LTS releases for anyone except hard-core software developers. Normal people need more than 6-9 months of support.

I've written many times in these forums about the risks of using .deb packages directly and using unmaintained PPAs. No need to repeat it again.  "DEB-Hell" is the result  ---  "RPM-Hell" is a similar thing for RPM-based distros.  There are 1,000 reasons to have excellent, versioned, backups.  This is just 1 of them. Please get backup religion after this, so the next time it is only a minor inconvenience.

OpenFoam/OpenFlow didn't exist when I was studying CFD. Looks like an amazing tool.  We wrote FORTRAN for every specific problem, which isn't efficient at all - especially for viscous boundary layer computations. ;(

---

### Post by Urs_Helfenstein on 2015-11-26
I am close to follow your advice of a new installation. But I have a lot of respect to do that.

I ran **dpkg --version** and the output was as follows:
```
Debian »dpkg« Programmversion der Paketverwaltung 1.15.5.6ubuntu2 (i386).
This is free software; see the GNU General Public License version 2 or
later for copying conditions. There is NO warranty.
See dpkg --license for copyright and license details.
```

When I google this dpkg version (1.15.5.6ubuntu2) it seems to be connected to version **10.04 (lucid)**. But my system runs with **14.04 (Trusty)**. Can it be that there was somehow a wrong dpkg version installed? If so, how is it possible to upgrade the dpkg version (e.g. to version 1.17.5ubuntu5.4)?
If this is the problem. How can something like this happen?

---

### Post by ian-weisser on 2015-11-26
Several ways.
It's most likely that the packager did not edit the string, or applied an old patch to that text.
It's possible, but less likely, the system used to be 10.04 (or 8.04, or 6.06), and has had unresolved upgrade problems for years.
It's also possible that you (or some other admin) deliberately downgraded dpkg, though that's quite unusual.

---

### Post by TheFu on 2015-11-26
Or some manually installed .deb file locked certain programs to specific versions preventing newer versions from being installed. dpkg isn't usually a hard dependency, but the underlying DB libraries could be - or a version of libc.

---

### Post by Urs_Helfenstein on 2015-12-10
Hi everybody, 

I was not able to fix it. But because I have a separete partition for '/home' and a colleague a similar installation, I had the possibility to clone the '/' partition and apt-get and dpkg works again. So I was able to run 'apt-get update' and 'apt-get upgrade' without any error. Than I tried which command mixed up my system and I found that the 'apt-get dist-upgrade' command fails and after that, the 'dpkg' package is missing and I have the same problems again. So clone the system and try to find the error. 

I removed all the ppa's and performe again 'apt-get update' and 'apt-get upgrade'. I found that most packages are listed as 'trusty' but a few under 'vivid'. 

Now the strange thing: I tried do see which distribution is really installed. If I go to 'System Settings' -> 'Details' the Ubuntu Version 14.04 is shown. But if I execute 'lsb_release -a' in the terminal the release 15.04 is shown.
Why is there a difference and how can I clean this up to be able to upgrade the distribution?

---

### Post by ian-weisser on 2015-12-10
> **Urs_Helfenstein said:**
> I found that most packages are listed as 'trusty' but a few under 'vivid'.
Please show us some of those 'vivid' package names.

---

### Post by TheFu on 2015-12-10
I didn't think it was safe to mix packages from different releases (trusty/vivid). How did that happen?
I think that is the root cause of the issue.

---

### Post by Urs_Helfenstein on 2015-12-10
So her the output of 'apt-get update'. At the top sometimes vivid is listed (bold):

```

dem@dem-EasyNote-TK81:~$ sudo apt-get update
[sudo] password for dem: 
Ign http://extras.ubuntu.com trusty InRelease                                                                                                                  
Holen: 1 http://security.ubuntu.com trusty-security InRelease [64.4 kB]                           
Ign http://ch.archive.ubuntu.com trusty InRelease                                                        
OK   http://extras.ubuntu.com trusty Release.gpg                                                         
OK   http://archive.ubuntu.com **vivid** InRelease                                   
OK   http://extras.ubuntu.com trusty Release                                     
OK   http://archive.ubuntu.com **vivid**/main amd64 Packages                         
OK   http://extras.ubuntu.com trusty/main Sources                                                                       
Holen: 2 http://ch.archive.ubuntu.com trusty-updates InRelease [64.4 kB]                                                
OK   http://archive.ubuntu.com **vivid**/main i386 Packages                                                                           
OK   http://extras.ubuntu.com trusty/main amd64 Packages                                                                          
OK   http://archive.ubuntu.com **vivid**/main Translation-de                                                                               
OK   http://archive.ubuntu.com **vivid**/main Translation-en                                                                                
OK   http://extras.ubuntu.com trusty/main i386 Packages                                                            
OK   http://ch.archive.ubuntu.com trusty-backports InRelease                                                            
OK   http://ch.archive.ubuntu.com trusty Release.gpg                                                                                                           
Holen: 3 http://security.ubuntu.com trusty-security/main Sources [101 kB]                                                                                      
Holen: 4 http://ch.archive.ubuntu.com trusty-updates/main Sources [247 kB]                                                                                     
Ign http://extras.ubuntu.com trusty/main Translation-de_CH                                                                                                     
Ign http://extras.ubuntu.com trusty/main Translation-de                                                                                                        
Ign http://extras.ubuntu.com trusty/main Translation-en                                                                                                        
Holen: 5 http://security.ubuntu.com trusty-security/restricted Sources [4'035 B]                                                                               
Holen: 6 http://security.ubuntu.com trusty-security/universe Sources [31.9 kB]                                                                                 
Holen: 7 http://security.ubuntu.com trusty-security/multiverse Sources [2'353 B]                                                                               
Holen: 8 http://security.ubuntu.com trusty-security/main amd64 Packages [382 kB]                                                                               
Holen: 9 http://ch.archive.ubuntu.com trusty-updates/restricted Sources [5'359 B]                                                                              
Holen: 10 http://ch.archive.ubuntu.com trusty-updates/universe Sources [145 kB]                                                                                
Holen: 11 http://ch.archive.ubuntu.com trusty-updates/multiverse Sources [5'167 B]                                                                             
Holen: 12 http://ch.archive.ubuntu.com trusty-updates/main amd64 Packages [665 kB]                                                                             
Holen: 13 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]                                                                       
Holen: 14 http://security.ubuntu.com trusty-security/universe amd64 Packages [120 kB]                                                                          
Holen: 15 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4'795 B]                                                                       
Holen: 16 http://security.ubuntu.com trusty-security/main i386 Packages [360 kB]                                                                               
Holen: 17 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]                                                                        
Holen: 18 http://security.ubuntu.com trusty-security/universe i386 Packages [120 kB]                                                                           
Holen: 19 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4'972 B]                                                                        
OK   http://security.ubuntu.com trusty-security/main Translation-en                                                                                            
OK   http://security.ubuntu.com trusty-security/multiverse Translation-en                                                                                      
OK   http://security.ubuntu.com trusty-security/restricted Translation-en                                                                                      
Holen: 20 http://ch.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]                                                                      
OK   http://security.ubuntu.com trusty-security/universe Translation-en                                                                                        
Holen: 21 http://ch.archive.ubuntu.com trusty-updates/universe amd64 Packages [332 kB]                                                                         
Holen: 22 http://ch.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.0 kB]                                                                      
Holen: 23 http://ch.archive.ubuntu.com trusty-updates/main i386 Packages [644 kB]                                                                              
Holen: 24 http://ch.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]                                                                       
Holen: 25 http://ch.archive.ubuntu.com trusty-updates/universe i386 Packages [334 kB]                                                                          
Holen: 26 http://ch.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.2 kB]                                                                       
Holen: 27 http://ch.archive.ubuntu.com trusty-updates/main Translation-en [329 kB]                                                                             
Holen: 28 http://ch.archive.ubuntu.com trusty-updates/multiverse Translation-en [6'832 B]                                                                      
Holen: 29 http://ch.archive.ubuntu.com trusty-updates/restricted Translation-en [3'699 B]                                                                      
Holen: 30 http://ch.archive.ubuntu.com trusty-updates/universe Translation-en [174 kB]                                                                         
OK   http://ch.archive.ubuntu.com trusty-backports/main Sources                                                                                                
OK   http://ch.archive.ubuntu.com trusty-backports/restricted Sources                                                                                          
OK   http://ch.archive.ubuntu.com trusty-backports/universe Sources                                                                                            
OK   http://ch.archive.ubuntu.com trusty-backports/multiverse Sources                                                                                          
OK   http://ch.archive.ubuntu.com trusty-backports/main amd64 Packages                                                                                         
OK   http://ch.archive.ubuntu.com trusty-backports/restricted amd64 Packages                                                                                   
OK   http://ch.archive.ubuntu.com trusty-backports/universe amd64 Packages                                                                                     
OK   http://ch.archive.ubuntu.com trusty-backports/multiverse amd64 Packages                                                                                   
OK   http://ch.archive.ubuntu.com trusty-backports/main i386 Packages                                                                                          
OK   http://ch.archive.ubuntu.com trusty-backports/restricted i386 Packages                                                                                    
OK   http://ch.archive.ubuntu.com trusty-backports/universe i386 Packages                                                                                      
OK   http://ch.archive.ubuntu.com trusty-backports/multiverse i386 Packages                                                                                    
OK   http://ch.archive.ubuntu.com trusty-backports/main Translation-en                                                                                         
OK   http://ch.archive.ubuntu.com trusty-backports/multiverse Translation-en                                                                                   
OK   http://ch.archive.ubuntu.com trusty-backports/restricted Translation-en                                                                                   
OK   http://ch.archive.ubuntu.com trusty-backports/universe Translation-en                                                                                     
OK   http://ch.archive.ubuntu.com trusty Release                                                                                                               
OK   http://ch.archive.ubuntu.com trusty/main Sources                                                                                                          
OK   http://ch.archive.ubuntu.com trusty/restricted Sources                                                                                                    
OK   http://ch.archive.ubuntu.com trusty/universe Sources                                                                                                      
OK   http://ch.archive.ubuntu.com trusty/multiverse Sources                                                                                                    
OK   http://ch.archive.ubuntu.com trusty/main amd64 Packages                                                                                                   
OK   http://ch.archive.ubuntu.com trusty/restricted amd64 Packages                                                                                             
OK   http://ch.archive.ubuntu.com trusty/universe amd64 Packages                                                                                               
OK   http://ch.archive.ubuntu.com trusty/multiverse amd64 Packages                                                                                             
OK   http://ch.archive.ubuntu.com trusty/main i386 Packages                                                                                                    
OK   http://ch.archive.ubuntu.com trusty/restricted i386 Packages                                                                                              
OK   http://ch.archive.ubuntu.com trusty/universe i386 Packages                                                                                                
OK   http://ch.archive.ubuntu.com trusty/multiverse i386 Packages                                                                                              
OK   http://ch.archive.ubuntu.com trusty/main Translation-de                                                                                                   
OK   http://ch.archive.ubuntu.com trusty/main Translation-en                                                                                                   
OK   http://ch.archive.ubuntu.com trusty/multiverse Translation-de                                                                                             
OK   http://ch.archive.ubuntu.com trusty/multiverse Translation-en                                                                                             
OK   http://ch.archive.ubuntu.com trusty/restricted Translation-de                                                                                             
OK   http://ch.archive.ubuntu.com trusty/restricted Translation-en                                                                                             
OK   http://ch.archive.ubuntu.com trusty/universe Translation-de                                                                                               
OK   http://ch.archive.ubuntu.com trusty/universe Translation-en                                                                                               
Ign http://ch.archive.ubuntu.com trusty/main Translation-de_CH                                                                                                 
Ign http://ch.archive.ubuntu.com trusty/multiverse Translation-de_CH                                                                                           
Ign http://ch.archive.ubuntu.com trusty/restricted Translation-de_CH                                                                                           
Ign http://ch.archive.ubuntu.com trusty/universe Translation-de_CH                                                                                             
Es wurden 4'235 kB in 3 min 24 s geholt (20.7 kB/s).                                                                                                           
Paketlisten werden gelesen... Fertig


```



And here the output of 'apt-get upgrade':

```

dem@dem-EasyNote-TK81:~$ sudo apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Paketaktualisierung (Upgrade) wird berechnet... Fertig
Die folgenden Pakete sind zurückgehalten worden:
  account-plugin-aim account-plugin-jabber account-plugin-salut account-plugin-yahoo accountsservice acpid alsa-utils anacron apparmor appmenu-qt5 apport
  aptdaemon apturl apturl-common at avahi-daemon bamfdaemon bluez brasero brasero-cdrkit brasero-common brltty bsdutils cheese cheese-common colord compiz
  compiz-core compiz-gnome compiz-plugins-default console-setup cpp cron cups cups-browsed cups-bsd cups-client cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers dbus deja-dup dnsmasq-base dpkg empathy empathy-common eog evince evince-common evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts file-roller fonts-thai-tlwg freerdp-x11 friendly-recovery g++ gcc gdb gfortran gir1.2-ebook-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-gdata-0.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0 gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-ibus-1.0
  gir1.2-networkmanager-1.0 gir1.2-rb-3.0 gir1.2-secret-1 gir1.2-totem-1.0 glib-networking glib-networking-common glib-networking-services gnome-calculator
  gnome-contacts gnome-disk-utility gnome-font-viewer gnome-keyring gnome-mahjongg gnome-mines gnome-orca gnome-power-manager gnome-screensaver gnome-session
  gnome-session-bin gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas gnome-sudoku gnome-system-monitor gnome-terminal
  gnome-terminal-data gsettings-desktop-schemas gstreamer1.0-clutter gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hplip hplip-data
  hud humanity-icon-theme ibus icedtea-7-jre-jamvm ifupdown imagemagick indicator-appmenu indicator-datetime indicator-keyboard init-system-helpers
  initscripts irqbalance isc-dhcp-client isc-dhcp-common kdelibs-bin kdelibs5-data kdoctools keyboard-configuration kmod libaccount-plugin-1.0-0
  libaccounts-qt5-1 libaccountsservice0 libalgorithm-diff-xs-perl libapparmor-perl libappindicator1 libapt-pkg-perl libbamf3-2 libbit-vector-perl libboost-dev
  libboost-program-options-dev libboost-system-dev libboost-thread-dev libbrasero-media3-1 libcheese-gtk23 libcheese7 libclone-perl libcloog-isl4
  libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcommon-sense-perl libcompizconfig0 libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl
  libcryptsetup4 libcups2 libcupscgi1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libcurl3-nss libdecoration0 libebackend-1.2-7
  libebook-1.2-14 libecal-1.2-16 libedata-book-1.2-20 libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libevdocument3-4 libevview3-3
  libfile-fcntllock-perl libfreerdp-plugins-standard libgail-3-0 libgbm1 libgcr-base-3-1 libgcr-ui-3-1 libgexiv2-2 libgl1-mesa-dev libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libgles2-mesa libgnome-keyring-common libgnome-keyring0 libgnomevfs2-0 libgnutls-openssl27 libgnutls26 libgoa-1.0-0b
  libgoa-1.0-common libgoa-backend-1.0-1 libgpod-common libgpod4 libgtk-3-0 libgtk-3-bin libgtkmm-3.0-1 libgtksourceview-3.0-1 libgweather-3-6 libhpmud0
  libhtml-parser-perl libhud2 libimobiledevice4 libio-pty-perl libjson-xs-perl libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4 libknotifyconfig4
  libkntlm4 libkparts4 libkpty4 libkrosscore4 libktexteditor4 libldap-2.4-2 libldb1 liblist-moreutils-perl liblocale-gettext-perl liblog-message-simple-perl
  libmm-glib0 libmouse-perl libmtp-runtime libmtp9 libmx-1.0-2 libmx-common libneon27-gnutls libnet-dns-perl libnet-ssleay-perl libnm-glib4 libnm-gtk-common
  libnm-gtk0 libnm-util2 libpam-modules libpam-modules-bin libpam-systemd libperlio-gzip-perl libplasma3 libpolkit-backend-1-0 libpolkit-gobject-1-0
  libpoppler-glib8 libpoppler-qt4-4 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple0 libpython3.4 libpython3.4-minimal libpython3.4-stdlib libqca2
  libqt4-dbus libqt4-declarative libqt4-designer libqt4-dev libqt4-dev-bin libqt4-help libqt4-network libqt4-opengl libqt4-opengl-dev libqt4-qt3support
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqt5core5a libqt5dbus5 libqt5feedback5
  libqt5gui5 libqt5multimedia5 libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5 libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5
  libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5 libqtcore4 libqtdbus4 libqtgui4
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-help-de libreoffice-help-en-us libreoffice-impress libreoffice-l10n-de libreoffice-math libreoffice-pdfimport
  libreoffice-style-human libreoffice-style-tango libreoffice-writer librhythmbox-core8 libsane-hpaio libsecret-1-0 libsignon-extension1 libsmbclient
  libsnmp30 libsocket6-perl libsolid4 libstreamanalyzer0 libstreams0 libsub-identify-perl libsub-name-perl libsystemd-daemon0 libtext-charwidth-perl
  libtext-iconv-perl libtext-soundex-perl libthreadweaver4 libtimezonemap1 libtotem-plparser18 libtotem0 libudev1 libunity-core-6.0-9 libunityvoice1
  libusbmuxd2 libuuid-perl libvncserver0 libwacom-common libwacom2 libwayland-egl1-mesa libwhoopsie-preferences0 libwhoopsie0 libxatracker2 libxml-libxml-perl
  libxml-parser-perl libxml2 libxml2-dev libxslt1.1 lightdm linux-generic linux-headers-generic linux-image-generic lsb-base mcp-account-manager-uoa
  mesa-common-dev metacity-common modemmanager mount mountall nautilus nautilus-data network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome ntfs-3g nvidia-prime nvidia-settings openjdk-7-jre openjdk-7-jre-headless perl perl-base perl-modules perlmagick plymouth
  plymouth-label plymouth-theme-ubuntu-text poppler-utils ppp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-hpcups printer-driver-hpijs
  printer-driver-postscript-hp procps protobuf-compiler pulseaudio pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils
  python-aptdaemon python-aptdaemon.gtk3widgets python-ldb python-lxml python-pycurl python-qt4 python-samba python-tk python-twisted-core
  python-twisted-names python-twisted-web python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-distupgrade python3-lxml
  python3-pyatspi python3-uno python3.4 python3.4-minimal qdbus qt4-designer qt4-dev-tools qt4-linguist-tools qt4-qmake qtdeclarative5-accounts-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-window-plugin remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc resolvconf rfkill
  rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rsyslog
  samba-common samba-common-bin samba-libs seahorse shotwell shotwell-common signon-plugin-oauth2 signon-ui signond simple-scan smbclient
  system-config-printer-common system-config-printer-gnome system-config-printer-udev systemd-services systemd-shim telepathy-gabble telepathy-salut totem
  totem-common totem-plugins transmission-common transmission-gtk ubuntu-desktop ubuntu-drivers-common ubuntu-minimal ubuntu-mono ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk ubuntu-session ubuntu-standard ubuntu-wallpapers udev udisks2 ufw unattended-upgrades unity unity-asset-pool
  unity-control-center unity-control-center-signon unity-greeter unity-services unity-settings-daemon unity-voice-service unity-webapps-qml uno-libs3 upower
  upstart ure ureadahead usbmuxd util-linux uuid-runtime vino webapp-container webbrowser-app whoopsie whoopsie-preferences xdiagnose xorg xserver-xorg
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 532 nicht aktualisiert.


```

I do not know if this is a problem. I deleted all the PPA's. Before more packages with vivid were listed. I have also no idea how this could happen. May be it was updated automatically while the computer was forced to shut down? Sometimes it run over night and I use Sentinella to shot it down if the calculation is done.

---

### Post by ian-weisser on 2015-12-10
Very bad.
Mixing sources intended for different releases of Ubuntu rarely ends well. While reasonably alike, the packages from different releases are not intended to be compatible.
Be prepared to backup your data and reinstall.

But there is a chance we can salvage it.
Please show us the complete contents of your file /etc/apt/sources.list
Please show us the complete contents of all files in the directory /etc/apt/sources.list.d/

---

### Post by Urs_Helfenstein on 2015-12-11
'/etc/apt/sources.list' is empty. I deleted all files there to remove the PPA's.

The content of '/etc/apt/sources.list' is as follows:

```
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ch.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ch.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ch.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ trusty universe
deb http://ch.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ch.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://ch.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ch.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://archive.ubuntu.com/ubuntu/ **vivid** main


```

At the end 'vivid' is mentioned.

---

### Post by ian-weisser on 2015-12-11
Yes, that last 'vivid' line is the cause of many problems. Delete it.

The theory of repairing is simple. In practice, it may be simple...or tedious.
1) Fix the sources by deleting that 'vivid' line.
2) Delete your local package cache (sudo apt-get clean) to eliminate already-downloaded vivid packges
3) Rebuild your package database using only the Trusty sources (sudo apt-get update)
4) Test the package manager (sudo apt-get upgrade)

When you hit step four, there are several possibilities.
It's possible that the package manager will work just fine. If so, run out and buy a lottery ticket and start chatting up the pretties - it's your luckiest day ever.
More likely, you will start discovering already-installed Vivid packages that cause apt errors. You must find and uninstall each of those Vivid packages. That's the tedious bit, and that's why reinstall might be more worthwhile.

---

### Post by Urs_Helfenstein on 2015-12-11
I didn't delete this line but replaced 'vivid' with 'trusty'. All the steps went through without any error or warning. I will chatting today with the pretties. That's a good idea ;)

So from this end it looks good. Just when I execuete 'lsb_release -a' the output still said that my system runs on vivid:

```

dem@dem-EasyNote-TK81:~/CodeAster/0_Projects/25_VibratoryDynamics/18_VibratoryPullPlateHarmonicExitation-ThermalExpansion$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


```

Should I risk an execution of 'sudo apt-get dist-upgrade' to update it to vivid?

---

### Post by ian-weisser on 2015-12-11
You already had a 'trusty main' repo on Line 5. You have created a needless duplicate.

lsb_release will probably continue to believe you are on vivid. It's not omniscient - it's simply reading a string somewhere. Expect other minor strangeness and minor breakage - the leftover scars of your Vivid experiment.

'dist-upgrade' will NOT upgrade you to Vivid. That's a (old) Debian technique, but doesn't work that way on Ubuntu. dist-upgrade will merely upgrade your kernel, if any kernel updates are pending for your release of Ubuntu. Upgrading from 14.04 directly to 15.04 is untested and unsupported - don't do it.

---

### Post by Urs_Helfenstein on 2015-12-11
Okay. Then I think it is done. Thanks to everybody who contributed with help and advices!

---

