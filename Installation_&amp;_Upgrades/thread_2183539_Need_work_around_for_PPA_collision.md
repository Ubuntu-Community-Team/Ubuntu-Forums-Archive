---
title: "Need work around for PPA collision"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by roland-logikalsolutions on 2013-10-25
There appears to be a nasty PPA collision.  This is a fresh install of OS/4 KDE which is basically repackaged KUbuntu 12.04 LTS.  I needed the latest LibreOffice for writing, BlueGriffon to update some Web pages, and Qt 5 to do some development.  Not an unrealistic or overly complicated request.

sudo add-apt-repository ppa:libreoffice/libreoffice-4-1

sudo apt-add-repository ppa:ubuntu-sdk-team/ppa

sudo apt-get update; sudo apt-get install libreoffice

sudo apt-get install bluegriffon

roland@roland-desktop:~$ sudo apt-get install qtdeclarative5-dev
[sudo] password for roland: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
qtdeclarative5-dev is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 qtbase5-dev : Depends: qtchooser but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
roland@roland-desktop:~$ 


roland@roland-desktop:~$ sudo apt-get install qtchooser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgucharmap-2-90-7 libgrantlee-gui0 libkdgantt2-0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  qt4-default qt5-default
The following NEW packages will be installed:
  qtchooser
0 upgraded, 1 newly installed, 0 to remove and 358 not upgraded.
44 not fully installed or removed.
Need to get 0 B/15.3 kB of archives.
After this operation, 73.7 kB of additional disk space will be used.
(Reading database ... 173180 files and directories currently installed.)
Unpacking qtchooser (from .../qtchooser_0.0.1~git20121229.g8f08405-0ubuntu1~precise1~test7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/qtchooser_0.0.1~git20121229.g8f08405-0ubuntu1~precise1~test7_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/qdbus', which is also in package qdbus 4:4.8.2+dfsg-2ubuntu1~precise1~ppa5
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/qtchooser_0.0.1~git20121229.g8f08405-0ubuntu1~precise1~test7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



I don't want to just uninstall qdbus package without knowing the new will work with old.  Qt 5 is not completely compatible with Qt 4.

Thanks,
Roland

---

