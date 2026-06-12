---
title: "Finding GNOME"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by zoom on 2006-08-11
I just installed the Ubuntu Server for the first time and would like to install GNOME as well.  After reading the apt-get and apt-cache docs I tried searching for a Gnome application grouping (similiar to yum groupings) ie: gnome-desktop-environment, however I was unable to find it.  I checked my /etc/apt/sources.list and from what I can tell it should be able to located it.  I'm I missing something???

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

---

### Post by unisol on 2006-08-11
did  you install the server install from the desktop cd if so put the cd in and do sudo apt-get install ubuntu-desktop

---

### Post by zoom on 2006-08-11
unisol,
  Thanks for your reply..  I installed Ubuntu Server using the Ubuntu Server Install CD...

---

### Post by unisol on 2006-08-11
you may need to sudo apt-get install linux-386 to get the kernel that handles the desktop then you have to sudo apt-get install ubuntu-desktop you may need to boot into recovery mode and type dpkg-reconfigure -phigh xserver-xorg, then do an init2 you should have the desktop hope this helps i ve only used ubuntu for a year and im no wiz

---

