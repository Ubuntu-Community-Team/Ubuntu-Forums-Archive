---
title: "JRE Install problems"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by Valencik on 2005-09-28
Again a simple problem:


sudo apt-get install sun-j2rel.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2rel.5


Why not? How do I fix it.

---

### Post by Leif on 2005-09-28
please see another reply I wrote to the same question today :

[http://ubuntuforums.org/showpost.php?p=376099&postcount=2](http://ubuntuforums.org/showpost.php?p=376099&postcount=2)

---

### Post by Valencik on 2005-09-28
andrew@Valencik:~$ sudo gedit /etc/apt/sources.list

Made the changes, added "deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java" right before the "## Backports" saved....

andrew@Valencik:~$ sudo apt-get update
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Get:1 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages [2490B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release.gpg [189B]
Get:7 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages [2411B]
Get:8 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages [33B]
Get:9 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages [4182B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Ign [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) hoary Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Get:10 [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) hoary Release [840B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse Packages
Ign [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) hoary/java Packages
Get:11 [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) hoary/java Packages [986B]
Fetched 10.9kB in 2s (5349B/s)
Reading package lists... Done
andrew@Valencik:~$ sudo apt-get install sun-j2rel.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2rel.5

---

### Post by Leif on 2005-09-28
that's because you're trying to install sun-j2rel.5 instead of sun-j2re1.5 (l versus 1)

---

### Post by Valencik on 2005-09-28
HAH! That's hilarious. I'm sorry for wasting your time hahaha. I am in debt to you.

---

### Post by Leif on 2005-09-28
dude no problem, we've all done this at some point :razz: glad I could help

---

