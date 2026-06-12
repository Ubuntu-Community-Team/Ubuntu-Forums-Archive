---
title: "Problem dual booting Windows from a second disk."
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by SaberCat on 2012-10-06
Hi,
I just upgraded to Ubuntu 12.04 and have found that my boot option menu no longer contains an entry for Windows 7 that is located on a second disk. Here it the output from fdisk -l:

root@walterh-PC:/boot/grub# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005097d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   608518143   304258048   83  Linux
/dev/sda2       608520190   625141759     8310785    5  Extended
/dev/sda5       608520192   625141759     8310784   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x86c69001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       80324       40131   de  Dell Utility
/dev/sdb2   *       81920    20803583    10360832    7  HPFS/NTFS/exFAT
/dev/sdb3        20803584   976771071   477983744    7  HPFS/NTFS/exFAT

How do I get Grub to recognize Windows 7 on /dev/sdb2 and include it in the boot menu? Thanks in advance...

---

### Post by darkod on 2012-10-06
If everything is OK with the windows boot files, this shouldn't have happened.

The first thing to try is running in terminal:
sudo update-grub

If that doesn't detect windows on /dev/sdb2, there is some problem with its boot files.

---

### Post by SaberCat on 2012-10-07
Hi Darko,
Thanks for the reply. You are right. This morning when I booted the following boot option was there:

Windows 7 (loader) (on /dev/sdb2)

And it worked. I had run update-grub earlier. Maybe I just missed the boot option after that.

Anyway thanks soooo much!

---

