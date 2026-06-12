---
title: "Partitioning/Install"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by soccertwin03 on 2006-10-28
This is the first time I am attempting to dual boot.  I have only used XP in the past.  

I have to drives, C and D.  Drive C has Windows XP.  Drive D is a 120 GB seagate harddrive.  I have some files in Drive D which I don't want to lose.  

Here is my problem.

I downloaded the ubuntu 6.10 desktop iso and burned it onto a cd.  Then i booted ubuntu from the cd and attempted to create my partitions in drive D.  However, in GParted it tells me that drive D is unallocated and that the DiskLabelType is unrecognized.

This is the output of fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40060403712 bytes
240 heads, 63 sectors/track, 5174 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         611     4619128+  12  Compaq diagnostics
/dev/hda2   *         612        5173    34488720    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       15506   117225328+   7  HPFS/NTFS

```

the output of GParted is:

```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
automounting disabled
======================
Can't have a partition outside the disk!
```

Any ideas on how I should proceed with the partition/install?  Thank you in advance.

---

### Post by elint6 on 2006-10-28
D drive is NTFS....Linux doesn't use NTFS...that's why the DiskLabelType is unrecognized.

---

### Post by soccertwin03 on 2006-10-28
What should I do to partition this drive then, without losing my data if possible?

---

### Post by soccertwin03 on 2006-10-29
bump.

---

### Post by markymark on 2006-10-29
I think gparted does have problems with some of
the partition tables written by other software
including diskdrake, cfdisk and mandrake.
The ubuntu installer uses gparted, so you are a little
stuck unless the partition table can be read by parted.

There are several less ideal alternatives to proceed, 
a) add a third disk for linux.
b) borrow a third disk and backup your d: data before
erasing that partition and repartitioning using fdisk
c) back your data up onto dvd/cd first then repartition with fdisk
d) maybe parted/gparted doesn't like one of your disks,
e.g. the first one (1st partition looks odd to me); 
so you could try and run it
specifically on the second disk,
e.g. parted /dev/hda2
and if that worked you could resize it and make a linux partition
and swap for ubuntu
etc

in each case the ubuntu installer won't let you install
unless the partitions can be read by parted/gparted which is part of
the installer. So reading by fdisk alone seems not to be enough.
But if you do reasonable things with fdisk, it can sort the disk
(see below)

others have also had similar problems
[http://ubuntuforums.org/showthread.php?t=286931](http://ubuntuforums.org/showthread.php?t=286931)
[http://ubuntuforums.org/showthread.php?p=1676755](http://ubuntuforums.org/showthread.php?p=1676755)

best wishes,
Mark

---

### Post by soccertwin03 on 2006-10-29
is there anyway I can edit my partition table and make it GParted friendly?  I have the PowerQuest Partition Table editor and can make changes to my partition table for drive 2.

When I use Partitioninfo on drive 2 I get the following error:

```
Error #109: Partition ends after end of disk.
  ucEndCylinder (15505) must be less than 15505.
```

In the partition Table Editor I have the following settings for drive 2:

```
Type=07, Boot=80, Starting Cyl=0, Head=1, Sector=1, Ending Cyl=1023, Head=239, Sector=63, Sectors Before=63, Sectors=234450657
```

Anyone have any idea on what needs to be changed in order for GParted to be able to read the table?

Thank you in advance.

---

### Post by markymark on 2006-10-30
I guess if this partitioning software allows you to edit the disk, then you should just be able to make a change (e.g. a resize)  and rewrite the partition table & it may then be readable to gparted. But I think it would be a very dodgy to do this without a good backup of the partition data, as if there is a problem with the partition, with your windows data could well be lost for good.

On linux I've been most impressed in the past with diskdrake, which reads most things. This is available from the first boot cd of a mandriva or older mandrake cds. It seems to read most things and is not as fussy as gparted about what it sees initially. You could try that to resize your partition.
(Again, backup first.) 
gparted is great but only when it loads!!! :)

---

