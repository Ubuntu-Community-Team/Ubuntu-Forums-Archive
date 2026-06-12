---
title: "GParted wont recognise my partitions"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by sling-shot on 2006-12-15
I want to install Ubuntu on one of the partitions in my harddrive of 160GB SATA.
I have 4 FAT32 partitions, 3 ext3 partitions, 1 Linux swap partition. and one ext3 home partition.
All the partitions were created using DiskDrake of PCLinuxOS. WindowsXP SP2 recognised all FAT partitions and installed without any problem.
But Ubuntu partition manager (GParted?) wont see any of these partitions. It will just show the whole harddisk as a single unit of 159GB.
Why is this so? Is it angry because the partitions were created using its rival? ;) 
Please enlighten me.
I want to install Ubuntu, but i dont want the hassle of changing the whole hard disk partition structure.
I have kept a 10GB partition for Ubuntu reserved. And there is no free space left to partition.
Thanks,
-SS.

---

### Post by lha on 2006-12-15
> **sling-shot said:**
> 
Why is this so? Is it angry because the partitions were created using its rival?

Yes, it is. DiskDrake can do some weird partitioning. Take a look what 'sudo fdisk -l' tells you. You'll probably have to do some repartitioning if the alternate cd installer fails to understand your partition table, as well.

---

### Post by sling-shot on 2006-12-16
Right now i am on Windows. Will do that ASAP and report back,
Thanks,
-SS.

---

### Post by sling-shot on 2006-12-21
Here is the 'sudo fdisk -l' output for my harddisk:

Disk /dev/sda: 160.0 GB 160041885696 bytes
255 heads 63 sectors/track 19457 cylinders
[HTML]
Device	boot	Start	End	Blocks		Id	System
/dev/sda1	*	1	2610	20964793+	b	W95 FAT32
/dev/sda2		2611	19349	134456017	5	Extended
/dev/sda3		15272	16546	10241437+	83	Linux
/dev/sda4		16547	17821	10241437+	83 	Linux
/dev/sda5		2611	5873	26210016	b	W95 FAT32
/dev/sda6		5874	12400	52428096	b	W95 FAT32
/dev/sda7		12401	15010	20964793+	b	W95 FAT32
/dev/sda8		15011	15271	2096451		82	Linux Swap / Solaris
/dev/sda9		17822	18473	5237154		83	Linux
/dev/sda10	18474	19349	7036438+	83	Linux
[/HTML]
[Please note that Ubuntu LiveCD mode did not allow me to save the output of "sudo fdisk -l" anywhere on the hard disk. It simply did not mount it at all. Since the DVD Drive already had the Ubuntu CD i could not write it to a CD also. Finally i wrote all this down on paper and then manually entered into Notepad!!! :-)]

By the way the "My Computer" in Ubuntu identifies the partitions as they are correctly but it refuses to mount any of them. GParted however sees the disk as a whole unpartitioned disk of 160GB.

Thanks,
-SS.

---

### Post by lha on 2006-12-22
If you look carefully at your partition table, you'll see that sda3 and sda4, primary partitions, are inside your extended partition sda2! Most partitioners I know of do not understand this kind of partition table. The only exception is DiskDrake...

A solution for your problem is to repartition. You don't have to wipe your whole drive, though. If you just get those primary partitions out of your extended partition, you should be fine.

---

### Post by louieb on 2006-12-22
> **lha said:**
>  you'll see that sda3 and sda4, primary partitions, are inside your extended partition sda2! 
If you rearrange the output by start block you will see sda3 and 4 are  in between  sda8 and sda9. I did not know that this was possible. I  do know that GParted cannot do this. It is my understanding that an extended partition and the logical partitions it contains has to occupy contiguous space on disk.  
I see now that this is not the case. Not much help here, but thanks for the example  of a working system with a extended /logical partition split between different areas of a disk. 
After the partitioning screen if you don't do anything there is a screen that asks how you want to mount the different partitions on the disk. I wonder if at that time it would display the partitions and let you choose which partition to make /. Just a thought.
```
Device     boot       Start             End    Blocks        Id    System
/dev/sda1        *      1      2610      20964793+    b    W95 FAT32
/dev/sda2          2611    19349    134456017      5     Extended
/dev/sda5          2611      5873     26210016       b     W95 FAT32
/dev/sda6          5874    12400     52428096       b     W95 FAT32
/dev/sda7        12401    15010      20964793+    b     W95 FAT32
/dev/sda8        15011    15271        2096451      82    Linux Swap / Solaris
/dev/sda3        15272    16546      10241437+    83    Linux
/dev/sda4        16547    17821      10241437+    83     Linux
/dev/sda9        17822    18473        5237154      83    Linux
/dev/sda10      18474    19349       7036438+     83    Linux

```

---

### Post by sling-shot on 2006-12-22
Hmmm... so basically this means i am fried.....
Would there be ANY way of correcting this situation without mortal damage? ;-)
-SS.

---

### Post by vimico on 2007-01-04
I don't have any answer, yet - but I can confirm the problem.

I used cfdisk to parition my drive. 1 primary, 1 swap (as primary) and 2 logical partions (because a 3rd one is planned, which makes the total number of partions >4, the max. number for primary partions). All Linux partions, btw.

cfdisk, fdisk and the kernel recognize them without a problem. But when trying to install Egdy onto this system, GParted doesn't even recognize the first primary one correctly. ](*,)

Did I miss the magic word? If Gparted can not recognize anything but its own creations, then I don't think it belongs on an install disk.

[Some time later]

I just tried the Alternate Install CD. It does not recognize the partitions either. Strange....  This is the first time I encounter paritioners that can not recognize a partition table which the operating system has no problems with...

Very well... a few hours of copying are waiting.

---

### Post by lha on 2007-01-05
> **sling-shot said:**
> Hmmm... so basically this means i am fried.....
Would there be ANY way of correcting this situation without mortal damage? ;-)
-SS.

Removing sda3 and sda4 could help. If the installer then likes your partition table, you should be able to create logical partitions in the unused space.

---

### Post by sling-shot on 2007-05-06
[vimico]
Same feelings here. And this happens with such a basic and essential thing as partitioning!

[all]
Finally i went ahead and backed up my whole harddrive. Then got hold of a copy of Paragon Hard Disk Manager. It has a liveCD using which i deleted all the Linux partitions, Converted the extended into primary and then made the last FAT extended and created new partitions in there. Now I have my previous partition structure back in a commonly readable format.
By the way Paragon told me that many of my parititions were illegal!!! Uh oh :-)

Took me a whole week of meticulous planning and backin up.
-SS.

---

