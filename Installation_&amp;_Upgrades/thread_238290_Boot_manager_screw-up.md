---
title: "Boot manager screw-up?"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by starfailure on 2006-08-17
First off, I installed XP on my primary partition.  Next, I booted to qtparted and created the Linux and swap partitions (though I'd already made an extended partition for Fat32).  
After this, when I reboot all I get is "error loading operating system", and I assume it's trying to boot to XP, but I'm not even sure.  I hadn't installed Ubuntu yet, but it seems that every time I did something in qtparted, XP wouldn't be able to boot.

So, this time, I just went ahead and installed Kubuntu on my linux partition, let Grub install and figured maybe that would fix the problem.
Now, when I select XP in Grub, my machine either reboots automatically, or gives an error (something about the filesystem).

Now, is there an easy fix so I can boot to XP again?  Or, should I try to reinstall XP altogether then try to fix the bootmanager again?

---

### Post by starfailure on 2006-08-17
Disk /dev/hda: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       35015    17647371    7  HPFS/NTFS
/dev/hda2           35015      201617    83967534+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3          201619      238216    18445392   83  Linux
/dev/hda5           35015      116280    40957686    e  W95 FAT16 (LBA)
/dev/hda6          116281      197546    40957686    e  W95 FAT16 (LBA)
/dev/hda7          197547      201617     2051752+  82  Linux swap / Solaris


Grub menu contains:

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by jakobc on 2006-08-17
I have the same problem.

XP says something like volume not bootable right after the XP spash screen

---

