---
title: "wubi, ubuntu 12.04 LTS installs applications"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by mersey on 2012-11-14
I've tried installing Ubuntu 12.04 LTS with Windows XP using wubi.

Installation is great and goes smoothly. It sets up the dual boot etc.

Unfortunately it also installs loads of applications that I don't want  - LibreOffice for a start (is Ubuntu going the microsoft route of installing crapware!).

Fortunately wubi also uninstalls the lot (uncluding Ubuntu) by re-running it.

How can I get a clean installation of Ubuntu only and then install the applications I actually want?

P.S. I'm an Ubuntu novice

---

### Post by cwsnyder on 2012-11-14
You can look at the minimal install CD, but for that you must know package names of what you want to install, including which desktop environment and X or Wayland if you want a GUI.  Minimal install is just that: Command Line Interface only.

If you want a desktop set up, just go through and delete those (probably few) packages which you don't want.  None of the packages you will find in Ubuntu are like the Microsoft packages, including functions which few want.  They just try to set up a generic, _working_ desktop.

---

### Post by Frogs Hair on 2012-11-14
Wubi installs the same default applications that are included with any Ubuntu desktop installation.

In order to get a minimal installation using Wubi you would have download the minimal ISO and place it in a folder with Wubi .exe and start Wubi.

Wubi will install using the minimal iso from the folder instead of downloading the latest version from the web site.This worked for a friend of mine but there are no guarantees.(Try at your own risk) 

The folder name is not important but you will need to remove you current version first. It doesn't hurt to defrag after removing Wubi.     

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

