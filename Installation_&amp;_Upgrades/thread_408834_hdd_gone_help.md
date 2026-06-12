---
title: "hdd gone help"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by Jeevan25 on 2007-04-13
after this [http://ubuntuforums.org/showthread.php?t=408083](http://ubuntuforums.org/showthread.php?t=408083)

i installed xp on partition 2. now i can't read partition 1 from partion 2. i can't read it from linux and i can't read it from xp. how can i read it? pls help.

---

### Post by stump138 on 2007-04-13
I'm guessing from reading both posts that you have turned the original windows partition into a swap partition for your ubuntu install.  When you selected that for your swap drive you destroyed Windows (someone correct me if I'm wrong).

From your previous post I would:

1. Pray you keep good data backups :)

2. Install windows onto the HD, fully formatting it.

3. Run the ubuntu live cd need to create 2 new partitions.  Leave your windows install alone as you did before, and create a partition for '/'.  Create a "swap" partition of a few GB.  Your end result should look something like this:

/dev/hda1  NTFS
/dev/hda2 '/'
/dev/hda3 Swap 

GRUB should automatically configure during the install :)

---

### Post by Jeevan25 on 2007-04-13
so there is no way i can get the files from my hard drive?

---

### Post by Herman on 2007-04-14
> so there is no way i can get the files from my hard drive?There is still a chance, you should immedialtely download a copy of  [GParted -- LiveCD]("http://gparted.sourceforge.net/")__ and make sure it's the latest version. 
It has a program called TestDisk in it. Most software looks at your partition table to get info about what partitions and filesystems are on your hard drive. TestDisk works the other way around,  it can search you hard disk for the starting sectors of old partitions you deleted and re-write the details of them back to MBR. If the filesystem data in the strat blocks of those partitions is still in good condition you will get all your files back.

I recovered some partitions and got 100% of the files back with TestDisk recently, and that was even after the disk has new partitions formatted over the top of the old ones, but not with the same starting sectors, and no new data was added. It's well worth the time spent trying to see if TestDisk will work for you or not.

Regards, Herman :D

---

### Post by Jeevan25 on 2007-04-14
but according to fedora, the messed up hard drive's format is ntsf.

---

### Post by Herman on 2007-04-16
**TestDisk** HomePage   [TestDisk - CG Security]("http://www.cgsecurity.org/wiki/TestDisk")
> TestDisk can ***find*** lost partitions for **all** of these file systems: [LIST]
[*]BeFS ( BeOS )
[*]BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
[*]CramFS, Compressed File System
[*]DOS/Windows FAT12, FAT16 and FAT32
[*]HFS and HFS+, Hierarchical File System
[*]JFS, IBM's Journaled File System
[*]Linux Ext2 and Ext3
[*]Linux Raid[LIST]
[*]RAID 1: mirroring
[*]RAID 4: striped array with parity device
[*]RAID 5: striped array with distributed parity information
[*]RAID 6: striped array with distributed dual redundancy information[/LIST] 
[*]Linux Swap (versions 1 and 2)
[*]LVM and LVM2, Linux Logical Volume Manager
[*]Mac partition map
[*]Novell Storage Services NSS
[*]NTFS ( Windows NT/2K/XP/2003/Vista )
[*]ReiserFS 3.5, 3.6 and 4
[*]Sun Solaris i386 disklabel
[*]Unix File System UFS and UFS2 (Sun/BSD/...)
[*]XFS, SGI's Journaled File System[/LIST]     Helpful Sites [Using TestDisk to Recover a 'Lost' FAT32 Partition]("http://mirror.href.com/thestarman/testdisk.html")

Regards, Herman :D

---

