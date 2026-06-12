---
title: "dual boot install"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by randywolf244 on 2012-01-15
hey im attempting to dual boot on my windows 7 desktop. i have the pendrive that i used to install xubuntu on my desktop. when i go into my boot menu. it gives me a ton of options options like usb-hdd usb-fdd and like 4 others. i tried them all and on the two listed above it said something like configuration file not found. 

thanks
rander

---

### Post by BC59 on 2012-01-15
Usually is better to use CDs and not USBs. The USB installation gives more errors and the pendrive tends to fail after some use.
If you can, burn a CD and try to do the installation with it.

---

### Post by Mark Phelps on 2012-01-16
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

