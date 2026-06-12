---
title: "my hard drive needs some help!"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by yugugu on 2011-12-13
I couldn't install ubuntu wubi when it reports the root disk is undefined, please correct it from partitioning menu. I also tried to install directly to hard drive patition but failed too. 

Could not see any partition information from GParted, saying the whole disk is Unallocated. But still can install windows, and see every right partitions and use them nomally in both Windows and Ubuntu live.

This is my fdisk -l message:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75a7be5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    30716279    15357116    7  HPFS/NTFS/exFAT
/dev/sda2        30716280   488408129   228845925    f  W95 Ext'd (LBA)
/dev/sda5        30722048   440807520   205042736+   7  HPFS/NTFS/exFAT
/dev/sda6       440809472   488394751    23792640    7  HPFS/NTFS/exFAT

I think it helped, I need your solution, thank you!

---

### Post by Mark Phelps on 2011-12-13
Since you're running Windows, are you running Vista or Win7?

If so, please boot into Windows, open the Disk Management utility -- and tell us what you see in terms of the types of partitions.

Are they all Basic Volumes, or are they Dynamic Disks?

---

### Post by coffeecat on 2011-12-13
@yugugu, welcome to the forum.

There is a problem in your partition table:

> **yugugu said:**
> ```


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total [COLOR="Red"]488397168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75a7be5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    30716279    15357116    7  HPFS/NTFS/exFAT
/dev/sda2        30716280   [COLOR="Red"]488408129[/COLOR]   228845925    f  W95 Ext'd (LBA)
/dev/sda5        30722048   440807520   205042736+   7  HPFS/NTFS/exFAT
/dev/sda6       440809472   488394751    23792640    7  HPFS/NTFS/exFAT
```

The end sector of your extended partition is showing as beyond the end of the physical drive, which is an impossibility. This is why Gparted is reporting the whole drive as unallocated and why the installer is having difficulties.

You can fix this with a small app called fixparts, for which there are both Linux and Windows versions. See here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You can run the Linux version from a live Ubuntu CD, or you can run the Windows version if you prefer.

---

