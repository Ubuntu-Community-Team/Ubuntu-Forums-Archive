---
title: "Installation from within.."
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by CorruptDNA on 2011-02-01
I have the iso of ubuntu 10.10 downloaded and want to install it in (from inside.. ) directly from ubuntu 9.10 .. is it possible, or will i have to perform "sudo apt-get install upgrade" ?
i cannot boot from a cd and tried from a usb and failed as my computer did not detect it for some reason after even changing some of my settings .. 
It would be great if there was a simple and easy way to install ubuntu 10 from ubuntu 9 without using a cd simply by using the iso..

---

### Post by Frogs Hair on 2011-02-01
If you start the upgrade process from 9.10 I think your upgrade will come in the form of a download to 10.04 because upgrades are done in order unless your upgrade from lts 8.04 to lts 10.04.

Since you have the ISO it would be better to backup you files and do a clean installation.

---

### Post by CorruptDNA on 2011-02-05
not really what i meant, i mean when im using the ubuntu 9.10 can i extract the iso and run the installation from there?

---

### Post by oldfred on 2011-02-05
Do you have a separate partition? or can you create one. Gparted will only work on unmount partitions, so you are limited on what you can do.

This will boot an ISO from a hard drive.
Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

