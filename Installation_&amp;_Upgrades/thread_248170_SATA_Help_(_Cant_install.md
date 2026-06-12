---
title: "SATA Help :( Cant install"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by lynxus on 2006-08-31
Hey guys.

After many issues ive managed to get to teh stage of installing :) yay

Anyway.
Now i have another problem.

I have 2 Sata drives attached to a Sil3112 sata controller ( Asus a7n8x deluxe mobo )

Now i have 1 drive set into 3 partitions ( 2 are windows that i want to leave ) and one is ready for conversion .. Anyway.

The other drive is just 1 big windows partition.


.. This is the problem ..

Ubuntu only shows 1 of the drives in device manager ( the one with 3 partitions ) so thats ok i suppose..
The other drive doesnt show at all as detected ( They are both Maxtors )

When i run Gparted to do the changes it just sits there scanning for drives, and doesnt even seem to see the "detected" drive anyway..


Has anyone got any ideas on how to get ubunto to see both these drives correctly and at least be able to see enuf info to even look at the partition table ?


Thanks
graham

---

### Post by lynxus on 2006-08-31
OK this is even weirder...

fdisk -l shows them both? But only one is in device manager? and gparted wint look at them :(

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19928   139588785    f  W95 Ext'd (LBA)
/dev/sda5            2551        7649    40957686    7  HPFS/NTFS
/dev/sda6            7650       19928    98631036    7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+  42  SFS

---

### Post by lynxus on 2006-09-01
Bump

---

