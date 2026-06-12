---
title: "dual boot install with xp on second partition"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by tjksn on 2007-12-15
I have a Compaq PC that initially came with Vista, but because we were having sooooo many problems with performance I installed XP on it.  I did this by repartitioning the drive into two equal parts using a live 7.04 cd and then installing XP on the second partition.  Since I've been able to activate this install I would like to install Feisty on the first partition.  When Vista was still on it I would get an error in trying to install Linux (I think I was actually trying to install Fedora at that time).  If I install Feisty will it go on the first partition and still detect the XP install?  Or should I just go ahead an install it on the entire drive?  The only reason not to do this is my wife still prefers Windows at this point.  I'd like to have a Linux machine to test the stability for myself and get used to it more.

---

### Post by logos34 on 2007-12-15
If vista is gone and you're able to boot XP, then you should be able to install ubuntu without a problem into the empty space/first partition.  It will (or should) detect windows and add it to menu.lst, but grub will overwrite windows bootloader on the MBR.  When you reboot you should have a choice of linux or XP on the grub screen.

---

