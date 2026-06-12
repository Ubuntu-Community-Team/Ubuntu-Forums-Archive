---
title: "Can't Find Hard Drive(s)"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by hocmin on 2008-09-02
My system started having some issues so I decided to just upgrade.  Bought a new mobo, cpu, ram, and video card.  Was hoping I could just install this and boot with no problem using my preexisting hard drives.  Problem is, when I try, I get the following error: 

> Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
Reading all physical volumes.  This may take a while.

ALERT! /dev/mapper/lvmvolume-root does not exist.  Dropping to a shell!

This takes me to BusyBox.  Turns out I can't find the hard drives at all.  I've tried booting with the live CD, going through the install procecss, and looking from BusyBox.  No sd*'s in /dev.  I've got two WD 640gb SATA hard drives using LVM with 8.04.1.  Before my hardware problems, everything was working great.  The new motherboard is a GIGABYTE GA-EP45-DS3L LGA 775.

I'd appreciate any help.  Thanks

---

### Post by manishtech on 2008-09-05
BusyBox discussion thread.
[http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

---

