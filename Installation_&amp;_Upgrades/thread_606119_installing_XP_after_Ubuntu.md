---
title: "installing XP after Ubuntu"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by Borg on 2007-11-07
OK I have just built a new system

I have  500 gig SATA drive now and I have installed Ubuntu



```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009fceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5106     1951897+  82  Linux swap / Solaris
/dev/sda3            5107       60801   447370087+  83  Linux

```

I want to now split sda3 into 2 more partitions
a 40 gig Partition for XP and a 200 gig FAT32 partition for my music and other files

I have looked at doing this with GParted but there is no option to make any more partitions.

Any help on how I can do this please ?

---

### Post by bulldog on 2007-11-07
> **Borg said:**
> OK I have just built a new system

I have  500 gig SATA drive now and I have installed Ubuntu



```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009fceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5106     1951897+  82  Linux swap / Solaris
/dev/sda3            5107       60801   447370087+  83  Linux

```

I want to now split sda3 into 2 more partitions
a 40 gig Partition for XP and a 200 gig FAT32 partition for my music and other files

I have looked at doing this with GParted but there is no option to make any more partitions.

Any help on how I can do this please ?
If sda3 is empty you can use this one to create an extended partition and in that extended partition you can create logical partitions.
**But you can't install windows on a logical partition,it will not boot**

---

### Post by Pumalite on 2007-11-07
Bad idea. To install XP first is best.

---

### Post by Borg on 2007-11-07
OK Ill junk this install and stick XP on first

---

