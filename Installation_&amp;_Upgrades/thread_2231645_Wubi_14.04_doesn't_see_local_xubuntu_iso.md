---
title: "Wubi 14.04 doesn't see local xubuntu iso"
date: 2014-06-26
forum: Installation &amp; Upgrades
---

### Post by robert94 on 2014-06-26
I trying to install Xubuntu 14.04 using Wubi 14.04 on Windows 7

I have the xubuntu-14.04-desktop-i386 iso in the same directory as Wubi but wubi doesn't not see it and keeps trying download ubuntu 14.04

What is going on ?

---

### Post by Bucky Ball on 2014-06-26
Best advice? Don't. Canonical no longer support Wubi. Please read here for forum staff recommendations:

Wubi recommendations:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

You are best off attempting a regular dual-boot; Ubuntu on one partition, Windows on another.

---

### Post by hakuna_matata on 2014-06-27
> **robert94 said:**
> I trying to install Xubuntu 14.04 using Wubi 14.04 on Windows 7

Wubi for Ubuntu 14.04 is not recommended. 
Wubi for Xubuntu 14.04 is not recommended _and_ not available: [http://ubuntu-with-wubi.blogspot.ca/2012/10/tricking-wubi-installing-xubuntu.html](http://ubuntu-with-wubi.blogspot.ca/2012/10/tricking-wubi-installing-xubuntu.html)

---

### Post by robert94 on 2014-06-28
All

Thank you for the replies & links. I just found it the past using Wubi easy to add and remove distros etc including Xubuntu 12.04

If I do the regular dual boot in a separate partition, how easy is it to uninstall any distro and remove/modify the dual boot grub menu etc

---

### Post by Bucky Ball on 2014-06-28
If you install the OS to the partition/mountpoint '/' and your personal data to /home or another partition, very easy. You just reformat the / partition if you want to use it for something else or simply install another distro into / and use the existing /home (you don't need to create a new one for every install generally. Same with /swap (2Gb). 

You can then run Boot Repair to fix grub booting. Remember, the grub is only active in one install. If you have, say, Win, Ubuntu and Xubuntu installed on three separate partitions, only the Ubuntu install or the Xubuntu install will be running the grub. If it was, say, the Ubuntu install which had its grub in the MBR, then you could remove Xubuntu without issue. 

This is all presuming your machine is not booting in UEFI mode, of course ...

---

