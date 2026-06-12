---
title: "hard drive issues at install"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by driven1 on 2011-05-25
Hello,
I have the problem that gparted cannot read the partition tables. I want to use some free space to install Natty, but the installer only sees the entire hard disk. I would also like to eliminate one of the two swap disks. I was looking at [_[COLOR="Blue"]this tutorial in the forums[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1192598") on how to use sfdisk but the thread appears to be inactive. I would appreciate some advice before I start making modifications. I have an XP primary partition. In the extended partition I have a 2.1gb XP backup file, then 76 gb that I use for shared storage between Linux Mint and XP, I have 40 gb allocated for Mint, 8gb unallocated, and two swap disks 1.1gb and 1.8gb. I need to fix this so I can use gparted. Thanks.

```

 sudo fdisk -l /dev/sda
omitting empty partition (10)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9358c633

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19458   125573737+   f  W95 Ext'd (LBA)
/dev/sda5            3825        4085     2096451    7  HPFS/NTFS
/dev/sda6            4086       13287    73907476    7  HPFS/NTFS
/dev/sda7           19327       19458     1049600   82  Linux swap / Solaris
/dev/sda8           14262       19113    38964224   83  Linux
/dev/sda9           19113       19327     1714176   82  Linux swap / Solaris

Partition table entries are not in disk order
```

here are the contents of the current PT.txt


```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 61432497, Id= 7, bootable
/dev/sda2 : start= 61432621, size=251147475, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 61432623, size=  4192902, Id= 7
/dev/sda6 : start= 65625588, size=147814952, Id= 7
/dev/sda7 : start=310480896, size=  2099200, Id=82
/dev/sda8 : start=229113856, size= 77928448, Id=83
/dev/sda9 : start=307044352, size=  3428352, Id=82
```

---

### Post by oldfred on 2011-05-25
I do not see a glaring problem. That it shows 19458 as last cylinder with drive having only 19457 may be just rounding as with LBA, cylinders are not used any more. I do not know to do math on sfdisk output but see no major overlaps.

Save a copy to the sfdisk output you posted to another device just in case.

I have seen gparted not work if NTFS partitions need chkdsk. It would not see my sda drive even though my XP booted. After chkdsk in windows then sda was available.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Fixparts - Repair broken partition tables (not overlapping issues)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Was drive ever in a RAID set? That can leave extra data that caused issues.

---

### Post by srs5694 on 2011-05-25
I also see no problems, with one possible exception:

```
omitting empty partition (10)

```

I'm not sure exactly what that means, although my guess would be that there's an Extended Boot Record (EBR) for a tenth partition, but the EBR doesn't define a partition. (An EBR is a data structure that contains information on a single logical partition. Usually there's exactly one EBR per logical partition, no more and no less.) If my guess is right, I don't know how libparted (upon which GParted is based) would react, although libparted can be pretty fussy, so it's conceivable it would react by showing a blank partition table.

If this analysis is correct, there are several possible fixes:


[list]
[*]Run [FixParts](http://www.rodsbooks.com/fixparts/) on the disk. This should eliminate the stray EBR. It will also detect if there are any overlapping partitions and omit one of them. (Thus, you should be sure to verify that they're all present before you save anything!) The FixParts Web page describes its use in detail, so please read it.
[*]Use fdisk to delete /dev/sda9. This will probably also delete the unused EBR, although I'm not 100% positive of that. Swap space is easily re-created, and you want to adjust it anyhow, so this shouldn't cause any problems.
[*]Take the sfdisk output you posted and feed it back, with "sudo sfdisk -f /dev/sda < PT.txt". This will rewrite the entire partition table and eliminate the stray EBR.
[/list]


One more comment, though: There's an unused chunk of space on the disk, between cylinders 13288 and 14261 (inclusive). This might be intentional or otherwise correct; however, it's conceivable that this "missing" tenth partition should exist in that space. Since it's not detectable by either fdisk or libparted, chances are following any of the procedures above won't make matters any worse; however, if there's important data in that space, you might want to use [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to recover it.

---

