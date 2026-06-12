---
title: "Problem with partitioning using gparted; any ideas?"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Najand on 2007-05-09
Well, let me explain about the situation first. I got an NEC LaVie computer from a friend. There were four partitions on it before;

1. Windows XP (NTFS): /dev/hda1
2. Debian Linux (Ext3): /dev/hda2
3. Swap Partition (sw): /dev/hda5 
4. Recovery Partition* (FAT32): /dev/hda4 
* /dev/hda4 which is the partiton came with this computer for installing Windows, Windows Drivers, etc. by NEC.

OK, I tried to remove EXT3 and SWAP partitions and format a new EXT3 and a new SWAP partitions (SWAP was pretty small; So I decided to make a bigger one)

I tried gparted on the Ubuntu live CD. And it faild during partitioning. When gparted reloaded the partition table, all partitions were gone and the was only one unallocated partition there.

I tried "fdisk -l" command and what I get is:
```

Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4256    34186288+   7  HPFS/NTFS
/dev/hda2            4257        8390    33206355    5  Extended
/dev/hda4            8391        9729    10755517+   c  W95 FAT32 (LBA)

```
And I can mount them using mount command without any problem.
However I am not able to use GNU Parted (GUI one and the old terminal one) to load the partiton table and re-partition them. 
Here is the Error I get after using parted to print the table;
> Error: Invalid partition table on /dev/hda -- wrong signature 0.


Well, i can remove the NTFS partition and Windows XP and install it again but I need the last partition (The FAT32 Recodery partition) and don&t want to lose data on it. 

The only solution I can think of is using an external harddisk and dd the FAT32 data on it and then re-partition the whole think. But still looking forward for eaiser solutions. I appereciate any helps (and ideas) in advance.

---

### Post by Najand on 2007-05-10
I could figure it out. I must be blind as it was all written there all the time, when I used fdisk command.

> Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)
Well, the solution is using:
Code:

```
sudo fdisk /dev/hda
```

It will repeat the above error. Then it will ask for command. By pushing "m" it will show all available commands and by pushing "w" it will rewrite the flag 0x0000 of partition table.

---

