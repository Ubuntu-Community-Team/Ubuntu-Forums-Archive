---
title: "Wants to overwrite whole disk"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by lift_test on 2011-01-08
I have reinstalled XP and conseqently messed up Grub and lost Ubuntu.  I am trying to do a fresh install but the installer insists on trying to overwrite the whole disk.  I downloaded the alternate instal ISO as this has got over this problem in the past but this also wanted to overwrite the whole disk. It recognises the Sata Raid array as being nfts (this is my main data disk) but it doesn't recognise the existing partitions on my main disk:
18G windows
18G Old Ubuntu
113G nfts data disk
Any suggestions please.

---

### Post by Rubi1200 on 2011-01-08
How do you know Ubuntu was lost? Are the files gone?

If you install Windows AFTER Ubuntu, all you have to do is reinstall GRUB to have the dual-boot option again.

From the LiveCD, post the output of ```
sudo parted -l
``` and ```
sudo sfdisk -V
``` and ```
sudo fdisk -lu
```

Thanks.

---

### Post by lift_test on 2011-01-08
I'l try those commands.  I presume that the old version is still on disk but I would like to install the latest version.

---

### Post by lift_test on 2011-01-08
Thanks  Results here:

ubuntu@ubuntu:~$ sudo parted -l
Error: Can't have overlapping partitions.                                 

Model: ATA WDC WD1200JD-00G (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      8225kB  120GB  120GB  extended               lba
 5      8258kB  120GB  120GB  logical   ntfs


Model: ATA WDC WD1200JD-00G (scsi)
Disk /dev/sdc: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      8225kB  120GB  120GB  extended               lba
 5      8258kB  120GB  120GB  logical   ntfs


Model: Linux device-mapper (mirror) (dm)
Disk /dev/mapper/pdc_ebhhcgjhi: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      8225kB  120GB  120GB  extended               lba
 5      8258kB  120GB  120GB  logical   ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label  

ubuntu@ubuntu:~$ sudo fdisk -v
fdisk (util-linux-ng 2.17.2)
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    36869174    18434556    7  HPFS/NTFS
/dev/sda2        36869175    95458229    29294527+  83  Linux
/dev/sda3        95458230   625137344   264839557+   f  W95 Ext'd (LBA)
/dev/sda4       360418338   598662224   119121943+   b  W95 FAT32
/dev/sda5        95458356   360418274   132479959+  83  Linux
/dev/sda6       598662288   625137344    13237528+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ca0db5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   234372284   117178110    f  W95 Ext'd (LBA)
/dev/sdb5           16128   234372284   117178078+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ca0db5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           16065   234372284   117178110    f  W95 Ext'd (LBA)
/dev/sdc5           16128   234372284   117178078+   7  HPFS/NTFS

Disk /dev/dm-0: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ca0db5b

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1           16065   234372284   117178110    f  W95 Ext'd (LBA)
/dev/dm-0p5           16128   234372284   117178078+   7  HPFS/NTFS

Disk /dev/dm-1: 120.0 GB, 119990352384 bytes
255 heads, 63 sectors/track, 14587 cylinders, total 234356157 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?   729050177  1273024900   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4      2692939776  2692991410       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by lift_test on 2011-01-08
If I start Ubuntu from live CD I get the results on previous post using a terminal but if I start GParted from System/Admin it shows sda as 298.09 Gib unallocated!  (also shows the sata as two separate disks)

Seems similar to Lusty's problem.

---

### Post by Rubi1200 on 2011-01-08
I don't know enough about RAID to help on that front.

But, it is a bit odd that fdisk said it was omitting sda5 and then reported it anyway.

The error from parted also bothers me:
```
Error: Can't have overlapping partitions.                                 
```

There are users on the forum with more experience in this area, so hang in there please until someone comes along with more suggestions.

---

### Post by lift_test on 2011-01-08
> **Rubi1200 said:**
> I don't know enough about RAID to help on that front.

But, it is a bit odd that fdisk said it was omitting sda5 and then reported it anyway.

The error from parted also bothers me:
```
Error: Can't have overlapping partitions.                                 
```

There are users on the forum with more experience in this area, so hang in there please until someone comes along with more suggestions.

RAID is not a problem, it's non recognition of the main drive that is the problem.  Presume no answer to the problem as no reply.

---

### Post by lift_test on 2011-01-12
> **Rubi1200 said:**
> I don't know enough about RAID to help on that front.

But, it is a bit odd that fdisk said it was omitting sda5 and then reported it anyway.

The error from parted also bothers me:
```
Error: Can't have overlapping partitions.                                 
```

There are users on the forum with more experience in this area, so hang in there please until someone comes along with more suggestions.

Still hanging but no replies.  Have noticed another (solved) thread which seems similar  ```
http://ubuntuforums.org/showthread.php?t=1662128
```  but am wary of trying this in case it messes up the SATA (all my data files) for XP.

---

### Post by lift_test on 2011-01-16
Have used various tools suggested on other threads and come to the conclusion that my main OS disk has become corrupt/damaged by multiple re-sizings etc.  The obvious solution would be to zap the disk and start again from scratch but as I have only just re-installed XP and finished loading everything else I was reluctant to start again.  All my data is on a 2 disk SATA Raid which I didn't want to disturb so I bought another 80 Gig IDE disk and loaded Ubuntu onto that.  This worked fine and I can boot whichever required now.  
Obviously when XP starts getting sluggish again I'll zap the disk completely before reloading.

It also found 10.04 which still runs fine.

---

