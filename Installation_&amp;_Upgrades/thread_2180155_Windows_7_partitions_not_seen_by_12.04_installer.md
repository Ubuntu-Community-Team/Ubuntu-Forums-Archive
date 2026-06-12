---
title: "Windows 7 partitions not seen by 12.04 installer"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by feelldream on 2013-10-11
when i installing ubuntu cannot see any drive int screen see like this
[ATTACH=CONFIG]246880[/ATTACH]
and when i see in windows like this
[ATTACH=CONFIG]246879[/ATTACH]
what should i do?? how to install ubuntu?? please help?? sorry for bad english ;)

---

### Post by Dreamer Fithp Apprentice on 2013-10-12
2 suggestions:

1- Try using gparted from the live disk. If it sees your partitions use it to set up a partition for your new installation and format it with a linux native file system (For what it's worth, I prefer ext3 because there are still some useful programs that can't deal with ext4 or the more exotic systems). I'm by no means sure that will work but it is worth a try. If that doesn't work, the only other thing I can think of is to try some other partitioning software. This is outside my experience. What Windows is this? Maybe they've introduced some new partitioning scheme to try to make it hard for people to install something else.

2-If you don't get help here in a day or so, you might try to start a new thread with a more descriptive title, perhaps "Windows [version] partitions not seen by 13.04 (or whatever version you are trying to install) installer". 

A title that describes a problem as precisely as possible is more likely to attract the attention of someone who thinks "Oh yeah, I had that problem once . . .".

All that of course is assuming you want to save part or all of what is on the drive now. If you don't care about saving anything on there it doesn't matter if the installer thinks it's an empty drive. Just treat like one, partition as you wish and format the new partitions.

---

### Post by feelldream on 2013-10-12
Thanks for replying. 
I use GParted from live disk again same
[ATTACH=CONFIG]246887[/ATTACH]
what should i do ???

Thanks

Bilguun

---

### Post by coffeecat on 2013-10-12
> **feelldream said:**
> Thanks for replying. 
I use GParted from live disk again same
[ATTACH=CONFIG]246887[/ATTACH]


The most probable explanation for seeing unallocated for the whole disc in Gparted when there are partitions present is an irregularity in the partition table. If this is so, it's easily fixed, but let's be sure this is the problem first. We'll need the output from a terminal command. From the Ubuntu live session, open a terminal and post the output of this command:

```
sudo fdisk -lu
```

You can copy and paste the output by highlighting the output with the mouse, right-click -> Copy, and then pasting it into the forum message editor with right-click -> Paste or ctrl-v. Please add [noparse]```
 and 
```[/noparse] tags around the output to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

You have another problem which will need to be addressed after this issue has been fixed and before you can install Ubuntu. If that is an mbr partition table, you have four primary partitions, the maximum number allowed. One will have to be deleted or converted to a logical partition.  Question: what is your E:, "server" partition for?

---

### Post by feelldream on 2013-10-12
E: disk is logical partition so here is a command
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4ef01f8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848  1433602047   716441600    7  HPFS/NTFS/exFAT
/dev/sda3      1433602048  1843202047   204800000    7  HPFS/NTFS/exFAT
/dev/sda4      1843202048  1953521663    55159808    f  W95 Ext'd (LBA)
/dev/sda5      1843204096  1953521663    55158784    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe6324093

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   156299263    78148608    c  W95 FAT32 (LBA)
```

---

### Post by coffeecat on 2013-10-12
> **feelldream said:**
> E: disk is logical partition 

It is indeed, but have another look at your Windows Disk Management screenshot in your first post. It's reporting it as a primary partition. It seems to be almost as confused as Gparted, and the probable reason is this:

> **feelldream said:**
> 
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! 

```

I can't find the other usual reasons for Gparted reporting unallocated (overlapping partitions; last sector of one partition beyond the physical end boundary of disc) so the cause is probably stray GPT data. This can happen if a disc is converted from a GPT partition table to an MBR partition table. Is this what has happened? Have you redone the partition table at any time? Is the 1000GB disc one recycled from use with a Mac?

Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

There are Linux and Windows versions available there.

---

### Post by feelldream on 2013-10-12
It's working now thank you!!!!!! i'm use the fixparts

---

