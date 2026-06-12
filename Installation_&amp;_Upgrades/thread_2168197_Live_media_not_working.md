---
title: "Live media not working"
date: 2013-08-16
forum: Installation &amp; Upgrades
---

### Post by jason13 on 2013-08-16
I just got a lenovo laptop and I wanted to test ubuntu with the hardware before going through the ordeal of installing it. I turned off UEFI boot mode and the same thing happened from both DVD and USB live disks. with the USB I get a prompt, try ubuntu on this computer et.al. and it seems like it's starting, then the screen just goes blank. From DVD I it goes right to the ubuntu loading screen, but before I get the option of "try" or "install" the screen goes blank. 

Edit: If I leave it going long enough ~1min I get the proper sound like Ubuntu has booted

---

### Post by Petro Dawg on 2013-08-16
Which version of Ubuntu are you trying to install (or load)?

---

### Post by jason13 on 2013-08-16
12.04 desktop 64-bit

---

### Post by Petro Dawg on 2013-08-16
Is this a brand new system, as in, a newer model?  If so, you might want to try the latest stable version of Ubuntu (13.04) to be sure you have support for the latest hardware.

---

### Post by jason13 on 2013-08-16
I have the Xubuntu version of 13.04 on dvd and it did the same thing. until I hit the power button, It didn't turn off completely, when I turned it on again I got the proper screen. it does however give me a system log error, i will try making recreating my USB drive with that version.

---

### Post by ubfan1 on 2013-08-16
Sounds like a video problem.  Try leaving UEFI mode set, then you should get a grub screen, type e to edit the grub commands, and add nomodeset to the linux line along with the quiet splash words.

---

### Post by jason13 on 2013-08-16
except in UEFI mode it boots to windows without giving me other options

edit: reset UEFI mode and got GRUB through the boot menu

edit (2): Got the splash screen, but it reverts to CLI (bash)

Edit (3): Got a live disk of ubuntu 9.10 (32bit) to boot to live mode

---

### Post by ubfan1 on 2013-08-16
Try a more current 64 bit release.  12.04.2 or later.

---

### Post by jason13 on 2013-08-16
I am using the latest release. just downloaded 2 days ago

Edit: got Ubuntu 10.04 to start. Had to use recreate my USB disk and useEFI mode, will install once I figure out how to do this with windows on the side.

---

