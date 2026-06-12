---
title: "ntfsresize: filesystem bigger than the device!!!"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by caesar753 on 2007-10-13
Hi all,
I caused a real mess installing newly ubuntu on my friend's laptop.
This is the situation:

I tried to use the resizer on the Ubutnu CD but it cannot resize the ntfs partition because there were two bad sectors. So i used ntfsresize and reduced the filesystem size fro 93 GB to 81 GB. Then i ran fdisk, deleted the old ntfs partion and created another one, but, perhaps because i made a mistake, smaller than the filesystem: it is about 75 GB!!! I continued in Ubuntu installation but now Windows cannot start. I'd like not to reinstall it but if i run again ntfsresize it tells me: 

> 
ntfsresize v1.9.4
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: **** bytes (***** MB)
Current device size: **** bytes (***** MB)
ERROR: Current NTFS volume size is bigger than the device!
Corrupt partition table or incorrect device partitioning?

Is there a way to resize again the ntfsfilesystem?
I cannot neither resize the device to 81 GB (the dimesion of the filesystem) because ubuntu has yet been installed and i don't want to delete and reinstall it.

Thanks...

---

### Post by Irony on 2007-10-13
I'm afraid its rather complicated!

Here are my notes for when I resized my windows XP partition from 60GB to 10GB. Note that first I resized the filesystem and then the partition.

This needed to be done from a liveCD or from a separate drive because my windows partition is first on my drive (before my ubuntu partition).

Note the [http://www.geocities.com/thekornerr/book/en_04.html](http://www.geocities.com/thekornerr/book/en_04.html) reference;

[PHP]Resizing ntfs
To determine minimum size;
irony@ubuntu:~$ sudo ntfsresize -if /dev/hda1
To resize;
irony@ubuntu:~$ sudo ntfsresize -f -s 10G /dev/hda1
Note this resizes the filesystem not the partition, this needs to be done in a separate operation.

Resizing Partitions with fdisk
See; http://www.geocities.com/thekornerr/book/en_04.html
7438 cylinders * 8225280 bytes = 61179632640 bytes

9999995392 bytes / 8225280 bytes = 1215.8 cylinders

+ 1 = 1217 cylinders

1 + 1217 - 1 = 1217

Start 1 End 1217
_________________

irony@ubuntu:~$ sudo umount /dev/hda1
irony@ubuntu:~$ sudo ntfsresize -if /dev/hda1
ntfsresize v1.9.4
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 9999995392 bytes (10000 MB)
Current device size: 61179600384 bytes (61180 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 7550 MB (75.5%)
Collecting shrinkage constrains ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :      3265 MB             0
Multi-Record       :      7661 MB             9
You might resize at 7549321216 bytes or 7550 MB (freeing 2450 MB).
Please make a test run using both the -n and -s options before real resizing!
irony@ubuntu:~$ sudo fdisk /dev/hda
Password:

The number of cylinders for this disk is set to 24792.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2            7439       20697   106502917+   5  Extended
/dev/hda3           20698       22451    14089005   83  Linux
/dev/hda4           22452       24792    18804082+  83  Linux
/dev/hda5            7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris
/dev/hda7           14619       16442    14651248+  83  Linux
/dev/hda8           16443       18509    16603146   83  Linux
/dev/hda9           18510       20697    17575078+  83  Linux

Command (m for help): d
Partition number (1-9): 1

Command (m for help): p

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2            7439       20697   106502917+   5  Extended
/dev/hda3           20698       22451    14089005   83  Linux
/dev/hda4           22452       24792    18804082+  83  Linux
/dev/hda5            7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris
/dev/hda7           14619       16442    14651248+  83  Linux
/dev/hda8           16443       18509    16603146   83  Linux
/dev/hda9           18510       20697    17575078+  83  Linux

Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
p
Selected partition 1
First cylinder (1-24792, default 1): 1
Last cylinder or +size or +sizeM or +sizeK (1-7438, default 7438): 1217

Command (m for help): t
Partition number (1-9): 1
Hex code (type L to list codes): 7
Changed system type of partition 1 to 7 (HPFS/NTFS)

Command (m for help): a
Partition number (1-9): 1

Command (m for help): p

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1217     9775521    7  HPFS/NTFS
/dev/hda2            7439       20697   106502917+   5  Extended
/dev/hda3           20698       22451    14089005   83  Linux
/dev/hda4           22452       24792    18804082+  83  Linux
/dev/hda5            7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris
/dev/hda7           14619       16442    14651248+  83  Linux
/dev/hda8           16443       18509    16603146   83  Linux
/dev/hda9           18510       20697    17575078+  83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource  busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
irony@ubuntu:~$[/PHP]

---

### Post by meierfra on 2007-10-13
I suggest to use "testdisk". It might be able to fix your partition table.

Information on testdisk can be found in [Hermanzone]("http://www.users.bigpond.net.au/hermanzone/p21.html")

---

