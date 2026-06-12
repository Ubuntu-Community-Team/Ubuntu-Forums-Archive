---
title: "Problem with swap partition"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by wedrowiec on 2011-07-30
Hi There!
I've install Ubuntu tonight but I already have 4 partition on my hard drive:
Recovery
Windows (100MB) -automatic
Windows (system)
Ubuntu
My problem is I'm not able to create Swap partition as I already have 4 existing (and it doesn't allow to create any more) do you know any solution to create one and keep all the other intact.
Thank you
Wedrowiec

---

### Post by oldfred on 2011-07-30
Welcome to the forums.

If you have already installed Ubuntu it is difficult to convert an existing primary partition to logical.

If reinstalling you create an extended partition for all the free space you want for added partitions. Then you can create as many logical partitions as you want in the extended partition. The extended partition is one of the four primary but is a container only for logical partitions.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Be sure to have good backups if you want to edit partition types.

This is more advanced and you have to have partitions that follow all the rules of partiitons. Only four primary, only one extended, all logicals have to be inside the one extended and perhaps a few more. Primarily for fixing issues, but can change partition types.

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325)

---

### Post by srs5694 on 2011-07-30
FixParts can convert between primary and logical partition types, but as oldfred says, you need at least one free sector before every logical partition. You can try FixParts and see if it will let you convert the Ubuntu partition into a logical; or you can post the output of the following command for more advice:

```

sudo fdisk -lu

```

Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to preserve the legibility of the columnar fdisk output.

---

