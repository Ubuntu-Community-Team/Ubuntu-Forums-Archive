---
title: "Feisty - installer doesn't recognize partitions"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by flyvholm on 2007-07-21
Trying to install Feisty on my Dell laptop w. 250GB HD. WinXP is on one partition, I have a FAT32 partition to share between WinXP and Linux, and then I've left some free space in which I was hoping to install Ubuntu. Unfortunately the installer doesn't recognize any partitions and only leaves me with the option to repartition the whole drive. I created the partitions partly with Partition Logic, but a Dell MediaDirect installation CD also automatically did some partitioning I had no control over (MediaDirect is a function that lets you play media without booting Windows, requiring a separate partition). The disk management utility in WinXP recognizes the partitions fine, as does fdisk:

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device     Boot    Start        End      Blocks        Id       System
/dev/sda1                 1          6       48163+       de       Dell Utility
/dev/sda2      *          7      22851   183502462+        7       HPFS/NTFS
/dev/sda3             22852      25401    20482875         c       W95 FAT32 (LBA)
/dev/sda4             25402      28213    22587358+        f       W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary
/dev/sda5             30140      30401     2104483+       dd      Unknown
```

That last one is the Dell MediaDirect partition. I'll post when I find a workaround; suggestions welcome. I am puzzled that there aren't consistent standards for such a crucial thing as partitioning... so many utilities that disagree, so many possibilites for getting your hard drive screwed up.

---

### Post by Pumalite on 2007-07-21
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by flyvholm on 2007-07-21
GParted is equally helpless; it also sees the whole hard drive as unallocated. :-|

---

### Post by Pumalite on 2007-07-21
Gparted is not helpless. It's the best partitioner around. Spend a little time with it and learn to use it.

---

### Post by flyvholm on 2007-07-21
Not saying GParted is generally helpless; indeed it would probably have created a partition table that the Ubuntu installer would recognize had I used it to do my partitioning in the first place.

But it doesn't help me in this case. The only option it provides me is the same as the Ubuntu installer: Repartitioning the whole hard drive. So I must look elsewhere to edit the partition table into something the Ubuntu installer understands.

---

### Post by flyvholm on 2007-07-25
I downloaded and tried several tools, e.g. Partition Table Doctor, which would warn me of errors but not fix them (without registration, xx dollars). Other tools will let you edit partition tables, but are unable to do any analysis to help you find errors. I was just about to give up and repartition everything from scratch when I tried:

[DFSee]("http://www.dfsee.com/")

Looks like a very powerful tool; seems capable of all the disk management tasks I've been looking for. It isn't free, but the trial is fully functional. I used its "Cleanup partition tables" and "Fix the Bootsector" functions (for the latter to become available you need to select the bootsector partition with "Open partition to work on"). I still get warnings about inconsistencies, but lo and behold, GParted now recognized my partitions and I was good to go with the Ubuntu installer as well. Problem solved.

---

