---
title: "Planning Repartition and Reinstall - Will GRUB Complain?"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by LucidForm on 2010-10-10
Hello,
I've been happily running Lucid Lynx for a few weeks in a dual boot setup with Win7. I unfortunately gave the /root partition too little space when installing, however, and have been considering deleting the partition and doing the install process over again (perhaps moving up to Maverick).

I plan to use the Win7 partition manager to delete the Ubuntu partitions. Will GRUB will allow me to boot the computer afterwards? Also, will GRUB be set up properly after I reinstall Ubuntu into the new and larger partition?

Thanks for your help!

---

### Post by LucidForm on 2010-10-11
Some help would be appreciated :roll:

---

### Post by dino99 on 2010-10-11
the good idea is: 
with winblows, use the winblows tools
with ubuntu, use the ubuntu/linux tools

but i think you dont need to start from scratch, if your / need more room, simply boot on partedmagic to modify the partition (expand)

[http://partedmagic.com/](http://partedmagic.com/)

usually you need:
- / about 12 gb with ext4
- swap: 2 gb
- /home: unlimited space with ext4

---

### Post by kansasnoob on 2010-10-11
> I plan to use the Win7 partition manager to delete the Ubuntu partitions. Will GRUB will allow me to boot the computer afterwards?

No, after deleting Ubuntu, Windows will not boot until you've either reinstalled Ubuntu or recovered the Windows mbr.

Dino99 is correct about using Windows own partitioning tools for Win7 and Vista partitions and Ubnutu's own tools for Linux partitions.

The Ubuntu Live CD/USB has Gparted (aka: Partition Editor) installed by default, it's in System > Administration.

It would be helpful to us if we had an idea what your partitioning arrangement looks like. You could begin by looking at, or posting, the output of:

```
sudo fdisk -l
```

As you can see in the example below it lists drive and partition designations, sizes, etc:

```
lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk **[COLOR="Red"]/dev/sdb[/COLOR]**: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054359

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1396    11205632   83  Linux
/dev/sdb2            1396        2796    11246592   83  Linux
/dev/sdb3            2796        4835    16380847   83  Linux
/dev/sdb4            4835        9730    39316481    5  Extended
/dev/sdb5            6818        9450    21147648   83  Linux
/dev/sdb6            9450        9730     2243584   82  Linux swap / Solaris
/dev/sdb7            4835        6729    15209472   83  Linux
/dev/sdb8            6729        6817      712704   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk **[COLOR="Red"]/dev/sda[/COLOR]**: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2610    20964793+  83  Linux
/dev/sda2            2611        5219    20956792+  83  Linux
/dev/sda3            5220       18363   105579180   83  Linux
/dev/sda4           18364       60801   340883173    5  Extended
/dev/sda5           39292       45992    53825751   83  Linux
/dev/sda6           45993       52514    52387933+  83  Linux
/dev/sda7           52515       59192    53641003+  83  Linux
/dev/sda8           59193       60495    10466316   83  Linux
/dev/sda9           60496       60801     2457913+  82  Linux swap / Solaris
/dev/sda10          36642       39291    21286093+  83  Linux
/dev/sda11          33998       36641    21237898+  83  Linux
/dev/sda12          31366       33997    21141508+  83  Linux
/dev/sda13          28691       31365    21486906   83  Linux
/dev/sda14          18364       20924    20571169+  83  Linux
/dev/sda15          20925       23487    20587266   83  Linux
/dev/sda16          23488       26089    20900533+  83  Linux
/dev/sda17          26090       28690    20892501   83  Linux

**[COLOR="Red"]Partition table entries are not in disk order[/COLOR]**

```

You'll notice that I highlighted my two drive designations, and at the end it says, "Partition table entries are not in disk order". Because of that I like to use "sudo parted <device> print" such as the example below:

```
lance@lance-desktop:~$ **[COLOR="Red"]sudo parted /dev/sda print[/COLOR]**
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary   ext3            boot
 2      21.5GB  42.9GB  21.5GB  primary   ext3
 3      42.9GB  151GB   108GB   primary   ext3
 4      151GB   500GB   349GB   extended
14      151GB   172GB   21.1GB  logical   ext4
15      172GB   193GB   21.1GB  logical   ext4
16      193GB   215GB   21.4GB  logical   ext4
17      215GB   236GB   21.4GB  logical   ext4
13      236GB   258GB   22.0GB  logical   ext4
12      258GB   280GB   21.6GB  logical   ext3
11      280GB   301GB   21.7GB  logical   ext3
10      301GB   323GB   21.8GB  logical   ext3
 5      323GB   378GB   55.1GB  logical   ext3
 6      378GB   432GB   53.6GB  logical   ext3
 7      432GB   487GB   54.9GB  logical   ext3
 8      487GB   498GB   10.7GB  logical   ext3
 9      498GB   500GB   2517MB  logical   linux-swap(v1)

lance@lance-desktop:~$ **[COLOR="Red"]sudo parted /dev/sdb print[/COLOR]**
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  11.5GB  11.5GB  primary   ext4            boot
 2      11.5GB  23.0GB  11.5GB  primary   ext4
 3      23.0GB  39.8GB  16.8GB  primary   ext4
 4      39.8GB  80.0GB  40.3GB  extended
 7      39.8GB  55.3GB  15.6GB  logical   ext4
 8      55.3GB  56.1GB  730MB   logical   linux-swap(v1)
 5      56.1GB  77.7GB  21.7GB  logical   ext4
 6      77.7GB  80.0GB  2297MB  logical   linux-swap(v1)

```

Notice I highlighted the exact commands. You can see that it lists all partitions in their actual order, easily read sizes, type of partition, etc :)

So if we could see the "parted" info it would be easier to recommend a repartitioning strategy.

---

### Post by LucidForm on 2010-10-11
Cheers, and thanks for the replies! Glad I asked before trying this :eek:

Here is the fdisk output:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1086     8721408   27  Unknown
/dev/sda2   *        1086       21711   165665792    7  HPFS/NTFS
/dev/sda3           21711       24322    20970497    5  Extended
/dev/sda5           21711       22458     5998592   82  Linux swap / Solaris
/dev/sda6           22458       23205     5998592   83  Linux
/dev/sda7           23205       24322     8971264   83  Linux
```and the parted output:
```

Model: ATA Hitachi HTS72202 (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  8932MB  8931MB  primary   ntfs
 2      8932MB  179GB   170GB   primary   ntfs            boot
 3      179GB   200GB   21.5GB  extended
 5      179GB   185GB   6143MB  logical   linux-swap(v1)
 6      185GB   191GB   6143MB  logical   ext4
 7      191GB   200GB   9187MB  logical   ext4
```sda1 is the recovery partition, sda2 is Win7, and sda3 is the extended partition encompassing sda's 5, 6, and 7. I have 3GB ram, hence the 6GB swap partition.

I would like to repartition sda2 for 125GB - Windows is fat, and I've got some games and engineering software that won't work in Ubuntu, so I can't shrink that partition more. This leaves 75GB for Ubuntu - 6GB swap, 12GB root, and 57GB home.

---

### Post by oldfred on 2010-10-11
Not really a monkey wrench in the works as what you have planned is fine, but you may also want another NTFS partition for sharing data between windows & Ubuntu. 

When I first started using Ubuntu and trying to figure it out, my wife would want to check email or get on the web and the bookmarks were missing from the windows thunderbird & Firefox. So I created a (back then FAT) a NTFS partititon (now) for some data and my firefox & thunderbird profiles. Then whichever system I booted email & bookmarks were identical. Some windows uses suggest a separate NTFS partition for data anyway, so when you have to reinstall windows your data is separate. 

I also prefer not to write into a system from a foreign system. So I read my windows system partition but only write into it for repairs. I also now keep all data out of all system partitions.

---

### Post by BingHeZhouKe on 2010-10-11
i have a question to consult,if grub installed at mbr,then after deleting ubuntu,could windows boot by grub?thank you

---

### Post by kansasnoob on 2010-10-11
> I would like to repartition sda2 for 125GB - Windows

**Absolutely use Windows own partitioner for that step!** It's much, much safer that way. Windows should stop you from damaging itself :)

When that step is complete I'd make certain that Windows still boots before repartitioning for Ubuntu. You'll find Gparted works fine to create the rest.

This will give you a pretty good idea how Gparted works:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

The installer has changed somewhat but the "manual partitioning" part of it is still quite similar.

Otherwise your plan sounds OK, I always put SWAP either at the beginning or end of the extended partition because resizing SWAP can sometimes change it's UUID which results in a minor (but fixable) nightmare. 

I also only "double" the size of RAM up to 1GB when calculating SWAP, then make SWAP slightly larger than total RAM for anything over 2GB, that is:

1GB RAM = 2GB SWAP
1GB to 2GB RAM = 2+GB SWAP
3GB RAM = 3+GB SWAP
4GB RAM = 4+GB SWAP
6GB RAM = 6+GB SWAP, etc.

But since you're a gamer it might be wise to keep SWAP at 6GB just in case you decide to add more RAM :)

If SWAP is less than total RAM it can prevent the use of Suspend and/or Hibernate.

---

### Post by kansasnoob on 2010-10-11
> **BingHeZhouKe said:**
> i have a question to consult,if grub installed at mbr,then after deleting ubuntu,could windows boot by grub?thank you

No. You'd need to restore the Windows bootloader.

Part of grubs files exist within the root partition (or boot partition if one exists).

---

### Post by LucidForm on 2010-10-11
> **oldfred said:**
> Not really a monkey wrench in the works as what you have planned is fine, but you may also want another NTFS partition for sharing data between windows & Ubuntu.

I agree - separating data and system files is a good idea! I would very much like to have a shared partition which holds OS-independent, user-created files. Windows, however, does not do a good job of organizing things this way. Many programs spew application data into the My Documents directory. For that reason I don't even use My Documents anymore. iTunes spews into the Music folder, and other directories can get equally ugly.

All my email is on the web, so that's okay. I'm considering using UbuntuOne to store all of my bookmarks and documents. This will also allow me to share between Ubuntu and Win7 when they finally roll out a Windows client for UbuntuOne :roll:.

---

### Post by LucidForm on 2010-10-11
> **kansasnoob said:**
> **Absolutely use Windows own partitioner for that step!** It's much, much safer that way. Windows should stop you from damaging itself :)

When that step is complete I'd make certain that Windows still boots before repartitioning for Ubuntu. You'll find Gparted works fine to create the rest.

Sage advice - thanks!

> **kansasnoob said:**
> I also only "double" the size of RAM up to 1GB when calculating SWAP, then make SWAP slightly larger than total RAM for anything over 2GB
Ah okay - I was using the 2 x ram rule I learned from back in the day when 1GB was a ton of ram!

---

