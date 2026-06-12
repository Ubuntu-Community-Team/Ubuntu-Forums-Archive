---
title: "Dual boot XP/Ubuntu problems"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by Soundislate on 2007-07-06
I tried installing Ubuntu on a XP system, but wrecked everything, so I formatted the disk and started over. I installed XP, then Ubuntu on two partitions on the same Raptor SATA disk. This worked out fine, but when I plug in two Western Digital SATA disks, I get error 22 on boot. I have a VIA VT6420 SATA RAID Controller on my mainboard. Is there any way to fix this?

---

### Post by Pumalite on 2007-07-06
If you installed a Raid Array with the last 2 drives, my guess is that you would have to reinstall again using dmraid driver. If not; you might get away with altering the boot order in BIOS according to what is logical to you. ( the drive the boot loader is in).

---

### Post by Soundislate on 2007-07-06
I'm sorry, I'm kind of a noob... What's a Raid Array? ;) 
Anyways, I doubt the problem is in BIOS. I recently moved the OS disk to SATA1 on the first controller on the motherboard, so I don't see why it would try to boot from the other disks I plug in...

---

### Post by dabl on 2007-07-06
I have a Silicon Image RAID controller on my motherboard, and I use WD Raptor SATA drives.  You need to just ignore the BIOS message from the RAID controller when you install Linux, and every time you boot.

You need to have all your drives plugged into the motherboard when you install the first OS (Win XP) and all subsequent OS's.  I think you're screwing up the OS by plugging in SATA drives after it thinks it knows your drive layout.  Just plug them all in, install Win XP like you want it (only format the partition where you want Win XP -- you don't want NTFS formats on the partitions where Linux runs).  Then install Ubuntu and let the Grub menu be placed where Win XP has its boot record. :)

---

