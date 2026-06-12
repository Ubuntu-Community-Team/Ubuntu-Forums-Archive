---
title: "Dual install, 2 HDD and Ubuntu sees all WinXP doesnt"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by FrancesL on 2010-01-11
:KS
I have 2 Hard drives, the original 30GBs with Windows XP on it, My son put 2nd hard drive into pc as slave (400GB), no problems, WinXP recognised 2nd drive. This was all a way to give 'good ole Mum' a chance to muck about with Linux..ok..Got a Linux Format Mag with Ubuntu 9.10 on it, amongst others, but this one I knew from previous use.
I have installed it on the 2nd hard drive, not sure if I correctly (manually) partitioned but I put ( I believe) a home partition, a swap partition, left ( so I thought) a 3rd partition space, and said install. Ubuntu runs fine and see the small HD with WinXP but WinXP doesnt see the HD with Ubuntu, and I wanted to use the 3rd partition for the WinXp as I need to use that for Grant writting I do for not for profit organisations govt depts that I apply for grants from are MS freaks, that said, all runs ok but what have I done that wont let WinXP see to utilise the 3rd partition. Be kind, I have a load of senior moments these days! LOL:P

---

### Post by vinnywright on 2010-01-11
frome in ubuntu post the output of (type in a terminal)

> sudo fdisk -l that is a lower case L not an I

it sounds like you made all the partitions on the second drive linux ext3 ext2 whatever

but post that and 

> df -hVINNY

---

### Post by prshah on 2010-01-11
> **FrancesL said:**
> Ubuntu runs fine and see the small HD with WinXP but WinXP doesnt see the HD with Ubuntu,

Click Start-Run and give the command```
diskmgmt.msc
``` Can you spot the second HDD?

If XP cannot see the HDD at all, then probably it may be a SATA HDD. If it is a SATA HDD, then you need to update your windows to at least Service Pack 2 (preferably service pack 3). It is a free download from Microsoft.

If it can see the second HDD but cannot recognize the partitions:
XP uses filesystems FAT(32) and NTFS. Ubuntu uses (primarily) ext2/3/4, which are not recognized filesystems for XP.

At this point, you have two options:

a) recommended: Format your 3rd (leftover) partition to NTFS; this way it is accessible to both Ubuntu and XP.

b) Install [Ext2/3 IFS drivers for Windows XP]("http://www.fsdrivers.org"). This will allow XP to read and write to Ubuntu partitions. Please be careful if you use this option, since there is a good chance that you can delete or otherwise affect important files in your Ubuntu installation.

Please post back with a screenshot of the disk management utility if you want more details.

---

### Post by FrancesL on 2010-01-11
> **vinnywright said:**
> frome in ubuntu post the output of (type in a terminal)

 that is a lower case L not an I

it sounds like you made all the partitions on the second drive linux ext3 ext2 whatever

but post that and 

VINNY
Disk /dev/sda: 40.1 GB, 40060403712 bytes
240 heads, 63 sectors/track, 5174 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x265f265f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5173    39107848+   7  HPFS/NTFS

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91ff101d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12168    97739428+  83  Linux
/dev/sdb2           12169       13384     9767520    5  Extended
/dev/sdb5           12169       13384     9767488+  82  Linux swap / Solaris
 
Then
frances@frances-HP:~$ df -h 
Filesystem            Size Used Avail Use% Mounted on
/dev/sdb1              92G  4.3G   83G   5% /
udev                  750M  272K  750M   1% /dev
none                  750M  216K  750M   1% /dev/shm
none                  750M   84K  750M   1% /var/run
none                  750M     0  750M   0% /var/lock
none                  750M     0  750M   0% /lib/init/rw

---

### Post by FrancesL on 2010-01-11
[QUOTE=prshah;8645339]Click Start-Run and give the command```
diskmgmt.msc
``` Can you spot the second HDD?

If XP cannot see the HDD at all, then probably it may be a SATA HDD. If it is a SATA HDD, then you need to update your windows to at least Service Pack 2 (preferably service pack 3). It is a free download from Microsoft.

Will look at this and post back.I have all current updates on WinXP.

Gut feeling tells me I didnt leave a NTFS partition..which is a big DUH...but no doubt someone such as yourself can tell me how to rectify.

---

### Post by FrancesL on 2010-01-11
:KS Followed the suggestions , opened diskmgmt.msc and yes could see the original C drive and the 3 partitions on the larger drive. With,yes you guesed it, 1 x unallocated 270GB.
So I have formatted that to NTFS and now I can both see it with Win XP and use it.
Thanks for your gentle and thoughtful handling of this. Now how do I mark it solved..hmmm;):D

---

