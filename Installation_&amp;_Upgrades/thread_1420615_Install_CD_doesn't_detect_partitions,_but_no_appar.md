---
title: "Install CD doesn't detect partitions, but no apparent overlapping partitions."
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by eremgumas on 2010-03-03
I'm having a problem with the Xubuntu 9.04 installation CD not detecting any of the current partitions.  This all started when I reinstalled windows XP a few days ago.  After, the computer wouldn't boot into GRUB and would boot directly into windows.

Other threads have dealt with a similar issue, that of overlapping partitions causing libparted/parted/gparted to detect the whole drive as unallocated space.  The problem in these threads seemed to be a corrupted partition table, in which the partitions overlapped with each other.  So of course I checked the output of fdisk -l for overlapping partitions, but I don't see any obvious overlapping partitions (unless I'm just missing something).

I've noticed that the partition that used to be linux swap isn't showing up in the partition table at all.

I might just be missing something simple here and would like another set of eyes to help me figure this one out.  Does the problem have anything to do with the partition table being out of order (ie. not in order of what regions they cover on the drive)?

From the liveCD I've run
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```and have received the following output:

```
 ubuntu@ubuntu:/mnt$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb289b289

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    58589054    29294496    7  HPFS/NTFS
/dev/sda2        58589055   100438379    20924662+   f  W95 Ext'd (LBA)
/dev/sda3        81931563   100438379     9253408+   b  W95 FAT32
/dev/sda4       100438380   115362764     7462192+  83  Linux
/dev/sda5        58589181    81931499    11671159+   b  W95 FAT32

ubuntu@ubuntu:/mnt$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 58588992, Id= 7, bootable
/dev/sda2 : start= 58589055, size= 41849325, Id= f
/dev/sda3 : start= 81931563, size= 18506817, Id= b
/dev/sda4 : start=100438380, size= 14924385, Id=83
/dev/sda5 : start= 58589181, size= 23342319, Id= b


ubuntu@ubuntu:/mnt$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.
```
GParted just shows the entire drive as unallocated space.

Thanks a million in advance.

---

### Post by sam.reader on 2010-03-03
This may be the last thing that you should try.
Try other channels before you try this.
Backup your data from your hard disk
Delete all the partitions and create new partitions.
This will most probably work

---

### Post by eremgumas on 2010-03-03
If I could figure out the problem and fix the partitions manually I would prefer that.  Otherwise I'd feel like I've been beaten.   Also, I don't have enough external storage to back up all the data on my drive.  ;)

---

### Post by eremgumas on 2010-03-06
Hmm, perhaps I originally posted the thread at a slow time.

---

