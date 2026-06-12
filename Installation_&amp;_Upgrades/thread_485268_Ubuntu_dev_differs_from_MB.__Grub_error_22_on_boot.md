---
title: "Ubuntu /dev differs from MB.  Grub error 22 on boot"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by dstud395 on 2007-06-26
Ok, I have a triple-boot environment with Windows Vista, XP, and Ubuntu.  I have a Windows bootloader for the 2 Windows OS's.  The problem is with Ubuntu.  My hard drives are attached to the MB as such:

SATA 0:  WD 250GB, primary 1: NTFS partition (Vista)
SATA 1:  Maxtor 250GB, primary 1: NFTS partition (XP)
SATA 2:  WD 500GB, primary 1: NFTS (Data); primary 2: ext3 (Ubuntu); primary 3: swap (Linux swap)

The problem is that Ubuntu mounts my drives as

/dev/sda1  (SATA 0: Vista)
/dev/sdb1, sdb2, sdb3 (SATA 2: Data)
/dev/sdc1 (SATA 1: XP)

So, when I configure grub, I tell it root (hd1,1) because this is how Ubuntu sees it.  But, grub is looking at the drives from the BIOS.  PROBLEM!!!!

As of now, both Windows are bootable, Linux is not.  I need to know how to make Ubuntu not stupid, and mount my drives in the right order.

---

### Post by logos34 on 2007-06-26
So you put Grub on the root partition (hd1,1)--not the MBR '(hd1)'--during the install process? Linux designated your sata drives according to BIOS boot order at the time, not in descending order of sata channels.  So far, so good. But what I think is happening based on the info you provided is that you are booting to drive sda where you are using the Vista bootloader for Vista and XP, but to boot Ubuntu you must be changing the drive order in the BIOS to go first to Grub on drive sdb.  As soon as you do that the linux drive sdb becomes (hd**0**) and Grub cannot find sdb because it is looking for it at (hd**1**).  

Try this: 

On the main kernel in the Grub menu screen hit 'e' to edit.  Change the 'root' line to '**(hd0,1)**' and make sure to hit Enter, then 'b' to boot.  But I'm not sure if that will be enough--you may have to use the live cd to edit device.map so that the linux drive reads

> (hd**0**) /dev/sdb

instead of (hd1).  (which means you will have to change the other drives to their new bios order)

---

