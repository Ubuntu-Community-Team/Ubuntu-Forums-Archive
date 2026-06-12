---
title: "Uninstall / Reinstall Help"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by jeremys07860 on 2007-11-13
Hello

I installed Ubuntu on a dual boot machine.. making it tri-boot

I have WinVista Ultimate, WinXP Home and Ubuntu 6.10

I would like to remove Ubuntu as I have it installed on another machine and this tri boot really does not work.  

How can I safely remve GRUB from my MBR and then delete the partition that Ubuntu created?

I attempted to just remove the partitions but upon reboot my machine still tried to load GRUB with no success (assumingly cause I delleted it) and would not load anything at all.  I reinstalled Ubuntu to the same partitions and it is fine now... I just realy dont want it on this machine.  

I built a machine specifically for Ubuntu... which leads to my next question
Can i dual or tri boot different versions of Ubuntu on the same machine without installing GRUB in 2 or 3 different places?

Any help is much appreciated

-Jeremy

---

### Post by taurus on 2007-11-13
If you remove Ubuntu, you also need to remove GRUB from MBR.  Either insert one of the windows CDs into a drive and boot into safe mode and fixmbr or use this program to remove GRUB from MBR.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

