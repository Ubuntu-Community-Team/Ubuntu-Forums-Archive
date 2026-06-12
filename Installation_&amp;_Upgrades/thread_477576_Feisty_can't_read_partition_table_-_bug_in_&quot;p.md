---
title: "Feisty can't read partition table - bug in &quot;parted&quot;? Workaround?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by uba704 on 2007-06-18
Hi!

I believe there might be a bug in "parted" and am looking for a workaround.

When I try to install Feisty and the installer comes to the partitioning step "Prepare disk space" I choose "Manual" and then it shows the partition table for /dev/sda as complete blank, but I know I have partitions there!

When I do from a console "sudo parted -s /dev/sda print" it tells me "Error: Can't have a partition outside the disk!". But the partition table should be ok since fdisk shows it for me without problems with "sudo fdisk -l /dev/sda". See below for the output.

Since I believe the Feisty installer uses "parted" for the partitioning process I believe there is some kind of bug in "parted". To get a workaround I would like to skip the partitioning part and have the installer continue with the installation. I have created the partitions for the installation with fdisk (/dev/sda5 and /dev/sda6) and formatted the root filesystem and set the label to '/' and created the swap.

QUESTION: How can I skip the partitioning part and pass relevant partition information to the installer? I would like to tell the installer to use  /dev/sda5 as swap and /dev/sda6 as '/' and skip the partitioning part. Is it possible? Maybe I can modify /usr/lib/ubiquity/bin/ubiquity in some way to avoid the partitioning part?

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5083    38420448+   7  HPFS/NTFS
/dev/sda2            9260       10122     6523728    7  HPFS/NTFS
/dev/sda3           10122       10338     1633808    7  HPFS/NTFS
/dev/sda4            5083        9259    31577560    5  Extended
/dev/sda5            5083        5471     2940248+  82  Linux swap / Solaris
/dev/sda6            5472        9259    28637248+  83  Linux

Partition table entries are not in disk order

---

### Post by Pumalite on 2007-06-18
> **uba704 said:**
> Hi!

I believe there might be a bug in "parted" and am looking for a workaround.

When I try to install Feisty and the installer comes to the partitioning step "Prepare disk space" I choose "Manual" and then it shows the partition table for /dev/sda as complete blank, but I know I have partitions there!

When I do from a console "sudo parted -s /dev/sda print" it tells me "Error: Can't have a partition outside the disk!". But the partition table should be ok since fdisk shows it for me without problems with "sudo fdisk -l /dev/sda". See below for the output.

Since I believe the Feisty installer uses "parted" for the partitioning process I believe there is some kind of bug in "parted". To get a workaround I would like to skip the partitioning part and have the installer continue with the installation. I have created the partitions for the installation with fdisk (/dev/sda5 and /dev/sda6) and formatted the root filesystem and set the label to '/' and created the swap.

QUESTION: How can I skip the partitioning part and pass relevant partition information to the installer? I would like to tell the installer to use  /dev/sda5 as swap and /dev/sda6 as '/' and skip the partitioning part. Is it possible? Maybe I can modify /usr/lib/ubiquity/bin/ubiquity in some way to avoid the partitioning part?

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5083    38420448+   7  HPFS/NTFS
/dev/sda2            9260       10122     6523728    7  HPFS/NTFS
/dev/sda3           10122       10338     1633808    7  HPFS/NTFS
/dev/sda4            5083        9259    31577560    5  Extended
/dev/sda5            5083        5471     2940248+  82  Linux swap / Solaris
/dev/sda6            5472        9259    28637248+  83  Linux

Partition table entries are not in disk order

What are you using: Vista or XP? if Vista, you have to partition FROM Vista. If XP, defrag several times, erase all temp files and get rid of stuff you don't need. Then use Gparted to make a partition with the rest, formatted ext3. Then install. During installation use 'Guided>Largest Available Space'

---

### Post by arvevans on 2007-06-18
Doesn't look like overlapping partitions, or any similar error:
BLOCKS:
[INDENT]1 to 5083 = HPFS (bootable)
5083 to 9259 = Extended Partition
[INDENT]5083 to 5471 = Linux Swap
5472 to 9259 = Linux root
[/INDENT]
9260 to 10172 = HPFS
10122 to 10338 = HPFS[/INDENT]

That puts Linux in an extended partition between two HPFS partitions, but should work that way.  

Hmmm...Try changing the Linux partitions so there is no overlap with the first HPFS partition assignment:
[INDENT][COLOR="Red"]5084[/COLOR] to 5471 = Linux swap
5472 to 9259 = Linux root[/INDENT]

Maybe will help, maybe not.
_._

---

### Post by arvevans on 2007-06-18
OOPs!  do the same thing with the 1st block of the extended partition.
_._

---

### Post by uba704 on 2007-06-18
Thanks for your answers!

The laptop is an HP Compaq nx7300 with Windows Vista pre-installed. I did use Vista's own partiton shrinkage tool for its main disk. The other two Vista-partitions (/dev/sda2 & /dev/sda3) were there from the beginning so I assume they are some kind of HP rescue/reinstall-thing or something and I guess it's wise to not remove them.

First time when I tried to install Ubuntu Feisty I just had shrinked the Vista main disk and nothing else. At that time there were no extended partition or Linux partitions. And when the installer came to the partitioning step the disk looked blank, exactly the same as now. Therefore I don't think the problem is the overlap of the two partitions at 5083. I think it's strange that "parted" says "Error: Can't have a partition outside the disk". A small overlap of two partitions at 5083 shouldn't be the cause of that error message, or what do you think? I suspect there is a bug in "parted" that it can't read the parition table of some strange reason.

But just in case I will try moving up the start of the extended partition from 5083 to 5084. I used fdisk and it suggested me to start the extended partition at 5083. I will try this tomorrow. Vista still works perfectly after I created those Linux partitions and formatted them.

Any workaround ideas are very welcome! I made a copy of /usr/lib/ubiquity/bin/ubiquity into /tmp/ and tried to have the installer skip the partitioning step. I then run the installer with "sudo /tmp/ubiquity" but I didn't succeed in skipping the partitioning step, probably because I am not that good at Python.

---

### Post by uba704 on 2007-06-19
Maybe "parted" says "Error: Can't have a partition outside the disk" because it misinterprets the size of the disk (80 GB) and think it's smaller than the actual size of some reason, what do you think?

Is there a way to get more verbose output from "parted"? I think that verbose output then might be visible when I run the installer from a terminal with "sudo /usr/lib/ubiquity/bin/ubiquity".

Another detail that might be related is that during boot up of the live CD I see error messages like this:

    [  43.812000] Buffer I/O error on device sda3, logical block 408451

(sda3 is the highest Vista-partition on the disk). That message showed up even before I did any partitioning with fdisk.

Thanks for any input!

---

