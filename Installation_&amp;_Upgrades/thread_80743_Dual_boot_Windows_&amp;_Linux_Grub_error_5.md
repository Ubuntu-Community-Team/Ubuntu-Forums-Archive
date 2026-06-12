---
title: "Dual boot Windows &amp; Linux: Grub error 5"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by Veniogenesis on 2005-10-22
Hi everyone!

I've been having trouble all day with installing Linux (Ubuntu) on a machine that already has Windows XP.  I was using Grub as the bootloader and it kept giving me Error 5 after my installation.  (I tried repartitioning and reinstalling for 5 times.)

I think it has something to do with the way I'm partitioning my drives.

This is my initial table:
> IDE1 Master (hda) - 160.0 GB
#1 primary 160.0 GB (BOOT) (NTFS) - /media/hda1

IDE2 Slave (hdb) - 200.0 GB
#1 primary 40.8 GB (NTFS) - /media/hdb1
#5 logical 139.7 GB (NTFS) - /media/hdb5
pri/log 19.5 GB FREE SPACE

SCSI1 (0,0,0) (sda) - 200.0 GB
#1 primary 200.0 GB (NTFS) - /media/sda1
This is what I was trying to use:
> IDE1 Master (hda) - 160.0 GB
#1 primary 160.0 GB (BOOT) (NTFS) - /media/hda1

IDE2 Slave (hdb) - 200.0 GB
#1 primary 40.8 GB (NTFS) - /media/hdb1
#5 logical 139.7 GB (NTFS) - /media/hdb5
#6 logical 830.7 MB (SWAP) - swap
#3 logical 18.5 GB (EXT3) - /
#7 logical 0.2 GB (EXT3) - /boot

SCSI1 (0,0,0) (sda) - 200.0 GB
#1 primary 200.0 GB (NTFS) - /media/sda1

Since I'm a newbie, I think I'm doing it TOTALLY wrong.  I was wondering if anyone could give me advice. ;)


Thanks so much!
Venio

---

