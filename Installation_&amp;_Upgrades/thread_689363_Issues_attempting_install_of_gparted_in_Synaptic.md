---
title: "Issues attempting install of gparted in Synaptic"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by bsamson on 2008-02-06
I am brand new to linux so please excuse me. I am trying to install gparted with Synaptic and i keep having issues w/ it asking for the Ubuntu disk. So, I put the disk in and it says it cannot mount the drive ... and I keep getting this popup saying, Would you like to open it with the package manager. If I hit cancel ... Synaptic reports the drive cannot be mounted ... if i hit START PACKAGE MANAGER from that popup window it does nothing. How do I fix this? Any assistance would be greatly appreciated!

---

### Post by dgray_from_dc on 2008-02-06
Click on Tools, then repositories.  Remove the CD from the active list.  This way you will get the latest version of the software downloaded from the online repositories.

---

### Post by klemens on 2008-02-06
well you probably have several dvd or cd drives.

easiest way to get around is to erase the cd from you're sources.list so it'll simply download the file

go to into a terminal

cd /etc/apt
sudo cp sources.list sourceslist.old (to make a copy of you're sources.list if you have some problems)
sudo gedit sources.list

then erase the first phrase about the cd and save

sudo apt-get update
sudo apt-get install gparted

---

