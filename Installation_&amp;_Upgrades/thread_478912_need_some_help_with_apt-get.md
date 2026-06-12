---
title: "need some help with apt-get"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by nimish on 2007-06-19
hey guys I am trying to install cacti in ubuntu. the tutorial says to install the following.

root@ubuntu:/etc/apt# apt-get install cgilib freetype2 libttf-dev libttf2 libpngwriter0-dev libpng3-dev libfreetype6-dev libart-2.0-dev snmp
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package freetype2

I keep getting the E: could not find package freetype2. any help would be appreciated. I am a noob to Linux.

---

### Post by swoll1980 on 2007-06-19
try sudo aptitude install somepakge

---

### Post by marc321 on 2007-06-19
Try libfreetype6 in place of freetype2.  That is the correct name for the FreeType 2 rendering engine and shared libraries in Ubuntu.

I found this out using Synaptic: System -> Administration -> Synaptic Package Manager, click Search, and search for freetype.

If you prefer the command line, *sudo aptitude search freetype* will tell you all packages that have freetype in the name or description.

---

### Post by nimish on 2007-06-20
thanks that worked. I am wondering how do i change my source.list to read from http instead of the cdrom. if you all are busy and can point me in the right direction. I wouldn't mind reading up on it and learning.

---

### Post by marc321 on 2007-06-20
This would be a good place to learn about package management in Ubuntu: [https://help.ubuntu.com/7.04/add-applications/C/index.html]("https://help.ubuntu.com/7.04/add-applications/C/index.html")

I think in your sources.list, just comment out any "deb cdrom" entries.

---

