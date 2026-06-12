---
title: "setting up a local repository"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by ArneLovius on 2006-09-29
Hi, 

I'm having a lot of trouble setting up a local repository.

I've already setup PXE booting (from Wndows....), but I could really do with a simple method of setting up a repository so that the rest of the install comes from a local server instead of over the Internet.

I've already tried using apt-mirror and debmirror, and on both of these the mirror appears to be complete but the installer complains that it was unable to download a file (and doesn't say what the file is).

Any pointers would be appreciated.

Cheers

---

### Post by pseudonym on 2006-09-29
Hi,

I don't know what your system/network environment is, but you can create a very simple repo like this - ```
sudo mkdir /usr/local/debs
copy all your packages to this directory
sudo -s 
dpkg-scanpackages debs /dev/null | gzip > debs/Packages.gz
``` Then you need to put your repo location into /etc/apt/sources.list. Are you using ftp to serve the files up? Then - ```
deb ftp://192.168.0.1/usr/local debs/
``` Now run - ```
sudo apt-get update
``` and your repo is ready to be accessed by your LAN.

HTH

---

### Post by ArneLovius on 2006-10-01
Hi, 

I think we are at cross purposes, I'm trying to create a local repository to install Ubuntu from, so that after doing a PXE boot, I can install install Ubunto from 'local sources' rather than pulling the entire install down over the internet.

Cheers

---

### Post by brainspank on 2006-12-29
Arnelovius, I think that pseudonym's post addresses part of your issue, as it sets up a repository.

However, I'm guessing you'll need to modify the Ubuntu install CD that you use to declare the proper repository (yours) in the sources.list.

I've never done this myself, but it seems logical...

---

