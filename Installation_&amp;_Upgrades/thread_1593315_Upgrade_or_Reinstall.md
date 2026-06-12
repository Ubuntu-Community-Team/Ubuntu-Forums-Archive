---
title: "Upgrade or Reinstall???"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by dioxholster on 2010-10-11
I want my personal files to remain and sstuff like Tomboy notes to be saved. I dont mind hours of installation or losing my customizations, all i care for are the files and a few softwares like VLC, chrome, transmission, celtx, etc.   So should i upgrade or reinstall? i never tried either of them.

---

### Post by BingHeZhouKe on 2010-10-11
> **dioxholster said:**
> I want my personal files to remain and sstuff like Tomboy notes to be saved. I dont mind hours of installation or losing my customizations, all i care for are the files and a few softwares like VLC, chrome, transmission, celtx, etc.   So should i upgrade or reinstall? i never tried either of them.

upgrade,it is safe and easy and any of your personal files or settings will be saved.:guitar:

---

### Post by mörgæs on 2010-10-11
- but if you nevertheless run into trouble, here is a solution:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1580857](http://www.uluga.ubuntuforums.org/showthread.php?t=1580857)

No matter what you do, best is to wait a few days.

---

### Post by dioxholster on 2010-10-11
So what will happen if I chose to reinstall or clean install? I mean what do most ubuntu users do? In windows i never upgrade, but Ubuntu I don't what will happen.

---

### Post by dino99 on 2010-10-11
cant give a good answer as we dont know how your installation is. Usually ubuntu is installed using 3 partitions:
- / : root partition bootable, ext4, about 12 gb
- swap: 2 gb
- /home: ext4, unlimited space, its where you store your data and settings

if your system is like that, then upgrading only happen into /, nothing change on /home (data are safe there)

If you want a fresh install, take care to install on the good partition: ie / (you need to know its name to select it, gparted give you this info, like /dev/sdx, x is from a to z), and use the "alternate" iso that let you choose the partition for a manual installation.

---

