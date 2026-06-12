---
title: "Resized filesystem, but how to resize partition"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by Irony on 2006-03-10
I've resized my ntfs filesystem in hda1 from about 50G to 15G;

[PHP]irony@ubuntu:~$ sudo ntfsresize -if /dev/hda1
ntfsresize v1.9.4
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 61179597312 bytes (61180 MB)
Current device size: 61179600384 bytes (61180 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 7955 MB (13.0%)
Collecting shrinkage constrains ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :      3265 MB             0
Multi-Record       :     36990 MB             9
You might resize at 7954546688 bytes or 7955 MB (freeing 53225 MB).
Please make a test run using both the -n and -s options before real resizing!
irony@ubuntu:~$
irony@ubuntu:~$ sudo ntfsresize -f -s 15G /dev/hda1
ntfsresize v1.9.4
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 61179597312 bytes (61180 MB)
Current device size: 61179600384 bytes (61180 MB)
New volume size    : 14999994880 bytes (15000 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 7955 MB (13.0%)
Collecting shrinkage constrains ...
Needed relocations : 168106 (689 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
100.00 percent completed
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/hda1'.
You can go on to shrink the device e.g. with 'fdisk'.
IMPORTANT: When recreating the partition, make sure you
  1)  create it with the same starting disk cylinder
  2)  create it with the same partition type (usually 7, HPFS/NTFS)
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before
Otherwise you may lose your data or can't boot your computer from the disk!
irony@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              14G  2.6G   11G  20% /
tmpfs                1015M     0 1015M   0% /dev/shm
tmpfs                1015M   13M 1002M   2% /lib/modules/2.6.12-10-386/volatile
/dev/hdb1             274M  8.0K  274M   1% /mnt/hdb1_fat32
/dev/hda4              18G   33M   17G   1% /mnt/hda4_ext3
/dev/hda7              14G  3.8G  9.3G  30% /mnt/hda7_ext3
/dev/hda8              16G  2.7G   13G  19% /mnt/hda8_Zenwalk
/dev/hda9              17G  2.1G   14G  14% /mnt/hda9_FC4
/dev/hda5              52G  2.4G   47G   5% /mnt/hda5_Ubuntu
/dev/hdb3             4.7G  2.5G  2.0G  57% /mnt/hdb3_Ubuntu
/dev/hdb4             3.5G  2.7G  669M  81% /mnt/hdb4_Zenwalk
/dev/hda1              14G  7.5G  6.6G  54% /mnt/hda1_XPHome[/PHP]

But I now want to resize the partition from about 50G to 15G. Gparted won't allow me to shrink it by more than a few megabytes, so how would I shrink it.
[IMG]http://www.ironclub.net/ubuntu/parts.png[/IMG]

---

### Post by plors on 2006-03-10
first of all, use an newer version of gparted (preferrably use the [gparted livecd]("http://gparted.sourceforge.net/livecd.php")).

then, you should have used gparted to resize your partition and your filesystem. The best thing for you to do right now is to resize this partition with gparted just a few MB. During the resize gparted will 'repair' the filesystem so it fits exactly in the partition again. After this you can resize it to it's final size and everything should be fine.

Have fun :) 

ps. of course you can also do
- ntfsresize /dev/hda1
- start gparted and do the resize (but please, use a newer gparted, since pre 0.2 releases may damage ntfs filesystems.)

---

### Post by Irony on 2006-03-11
I've already tried the gparted livecd but whilst it works on my laptop it doesn't on my desktop machined it gets stuck at opcode not recognised - I think this means it doesn't recognise athlon chips.

I've also tried gparted on this ubuntu and live cd ubuntu but in both cases when it comes to applying the resize of the ntfs partition it says **'device still mounted cannot complete operation'** - what this device is I don't know.

This is why I tried the sudo *ntfsresize -f -s 15G /dev/hda1* instruction which has resized the filesystem but gparted still won't allow partition resizing.

I'm wondering whether I can use cfdisk to delete this partition and then reset it as 15G or will this simply destroy the filesystem.

---

### Post by plors on 2006-03-11
[QUOTE=Irony]I've already tried the gparted livecd but whilst it works on my laptop it doesn't on my desktop machined it gets stuck at opcode not recognised - I think this means it doesn't recognise athlon chips.
[/QUOTE]
Sounds like a bug. Please file a [bugreport]("http://gparted.sourceforge.net/bugs.php") so the developers can have a look at it.

thanks!

---

### Post by cotcot on 2006-03-11
I suggest to do a drive check and defrag on the windows first.

---

### Post by Irony on 2006-03-11
I've done that - in fact it automatically does a check on start up, also I defragged windows again.

Windows shows the partition as shrunk from 50G to 15G but doesn't show the free space (the drive space appears lost) - so I still somehow have to shrink the partition rather than just the filesystem.

---

### Post by KansasJoe on 2006-03-11
partition magic will be your best friend when it comes to getting lost drive space back

---

### Post by Irony on 2006-03-12
Well its not lost - I'm sure I can get it back.

What I need is some non-gparted way of shrinking the partition so it matches the filesystem. Perhaps cfdisk, but it looks to me as if this would simply format the partition rather than resize it.

At the moment because I can't shrink the ntfs partition it means I can't shuffle the other partitions about.

---

### Post by cotcot on 2006-03-12
[QUOTE=Irony]
I've also tried gparted on this ubuntu and live cd ubuntu but in both cases when it comes to applying the resize of the ntfs partition it says **'device still mounted cannot complete operation'** - what this device is I don't know. [/QUOTE]

You have to unmount the XP partition first. The padlock on the screen shows that the partition is mounted. Right click on it and select "unmount" from the menu. Then you should be able to shrink the XP partition.

---

### Post by Irony on 2006-03-13
Yes I unmounted the partition first, in fact I unmounted pretty much everything, this is why I tried the Ubuntu live cd - I wonder if for some reason it doesn't like the mounted swap partition; I noticed that the live cd was actually using my hard drive swap partition.

---

### Post by az on 2006-03-13
[QUOTE=Irony]Yes I unmounted the partition first, in fact I unmounted pretty much everything, this is why I tried the Ubuntu live cd - I wonder if for some reason it doesn't like the mounted swap partition; I noticed that the live cd was actually using my hard drive swap partition.[/QUOTE]
Yes, that's why.

sudo swapoff -a


It should be super easy to resize this partition.  If you create another partition with the free space, the naming of the partitions that follow it will change and you will have to edit /grub/menu.list and fstab accordingly...

---

### Post by Irony on 2006-03-13
Okay I've solved it. This is what I did;

First I had resized the filesystem from 60G to 15G but I pressed the wrong number as I wanted 10G, so I did the operation again using ntfs resize;

[PHP]irony@ubuntu:~$ sudo umount /dev/hda1
irony@ubuntu:~$ sudo ntfsresize -if /dev/hda1
ntfsresize v1.9.4
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 14999994880 bytes (15000 MB)
Current device size: 61179600384 bytes (61180 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 7953 MB (53.0%)
Collecting shrinkage constrains ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :      3265 MB             0
Multi-Record       :      8523 MB         35500
You might resize at 7952592896 bytes or 7953 MB (freeing 7047 MB).
Please make a test run using both the -n and -s options before real resizing!
irony@ubuntu:~$ sudo ntfsresize -f -s 10G /dev/hda1
ntfsresize v1.9.4
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 14999994880 bytes (15000 MB)
Current device size: 61179600384 bytes (61180 MB)
New volume size    : 9999995392 bytes (10000 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 7953 MB (53.0%)
Collecting shrinkage constrains ...
Needed relocations : 262256 (1075 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
100.00 percent completed
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/hda1'.
You can go on to shrink the device e.g. with 'fdisk'.
IMPORTANT: When recreating the partition, make sure you
  1)  create it with the same starting disk cylinder
  2)  create it with the same partition type (usually 7, HPFS/NTFS)
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before
Otherwise you may lose your data or can't boot your computer from the disk![/PHP]

The first instruction determines what size I can shrink the filesystem to the second actually shrinks it.

I now had to shrink the partition (gparted and parted wouldn't do this despite help from ntfs tools). To do this I found [http://www.geocities.com/thekornerr/book/en_04.html](http://www.geocities.com/thekornerr/book/en_04.html) and so used fdisk to shrink the partition to slightly bigger than my shrunken filesystem;

[PHP]irony@ubuntu:~$ sudo umount /dev/hda1
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
Syncing disks.[/PHP]

The first instruction was simply ntfs resize again so I could look at Current volume size: 9999995392 bytes (10000 MB) and Current device size: 61179600384 bytes (61180 MB). I basically wanted to shrink the device down to just a bit bigger than volume. I thus did;

[I]   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS[/I]

down to;

[I]   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1217     9775521    7  HPFS/NTFS[/I]

7438 is the number of cylinders which times 8225280 bytes gives the total bytes of hda1, I therefore calculated 1217 would be about 10G. I now have about 50G of free space which I can use to shuffle the other partitions around.

---

