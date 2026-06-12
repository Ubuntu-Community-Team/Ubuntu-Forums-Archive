---
title: "Using apt-cdrom to make a CD recognizable to Synaptic"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by puffy1980 on 2007-01-16
Please help. I cant add my CD ROM to the sources in Synaptic. None of the web sites work either, probably because apt-get update or upgrade uses the ip address 1.0.0.0.0 which I know must be wrong.

This is the error message I get :

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)
cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/source/Sources.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Can anyone help? Im really new to Linux and dont even know where to begin. Using Breezy 5.10 if that helps.

---

### Post by puffy1980 on 2007-01-16
Doesnt matter, fixed it all on my own!!!! Major chuff on for me! If anyone else needs the same solution, edit /etc/resolv.conf and instead of the ip addy 192.168.1.1 use 203.8.183.1 Seems to be something to do with not having access to the net during install of Ubuntu. CHUFF CHUFF!!!!!

---

