---
title: "How to boot Win XP on local HD when external HD with Linux is unplugged?"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by SenseiDP on 2008-02-27
Hi all,

I am running a dual boot, with Ubuntu on an external HD and am working on repairing my copy of Win XP on my local hard drive.  I had everything working fine before Windows ate itself (unrelated to my current question) and was able to dual boot XP from local disk and Ubuntu from external without a problem.  I need to, however, be able to run my computer also without the external plugged in, and hence boot straight into XP (once I fix it, that is) by default.  I imagine there is a reasonably simple answer here.  Any help would be grand.  Cheers!

Dan

---

### Post by aashay on 2008-02-27
1) Fiddle around in the First boot device / Boot device order in the BIOS settings. 
2) Install GRUB on the non-removable HD which boots windows. Add entries to it to boot ubuntu on the external

EDIT: Try 2 only of 1 fails

---

### Post by SenseiDP on 2008-02-27
Could you possibly be more specific?  I'm not too advanced in the ways of Linux.  Thanks.

---

### Post by dstew on 2008-02-27
I think he means this:

1. Go into your BIOS setup and change the boot disk order so that the external disk boots before the hard disk. Install grub onto the external disk only. Then, when the external disk is plugged in, it will boot, but if it is not there, the internal disk will boot. Only some BIOSes will let you do that, though. Also, your BIOS has to be able to boot an external USB drive.

2. If you want to install grub onto the internal drive, and select the boot operating system from a grub menu, you will have to create a small partition on your internal drive to contain grub's stage2 and configuration file. Otherwise, when the external drive is not plugged in, you won't be able to get a grub menu.

---

