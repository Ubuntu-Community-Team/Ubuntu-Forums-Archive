---
title: "Partition 1 does not end on cylinder boundary"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by Devan Dean on 2011-10-04
I did a clean install of ubuntu 10.04.3 this morning. I usually use gparted to create the partitions, but decided that this time I would create them during the install process. I also decided to create a /boot partition, which is something I have never done before. The computer boots up with no problems.

I ran sudo fdisk -l and this is the output:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d4e7c     

Device   Boot      Start       End      Blocks   Id  System
/dev/sda1   *           1         122      975872   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             122        2554    19530752   83  Linux
/dev/sda3            2554        2797     1952768   82  Linux swap / Solaris
/dev/sda4            2797        4620    14647297    5  Extended

/dev/sda1 is a /boot partition. Is the fact that fdisk says "Partition 1 does not end on cylinder boundary." going to cause problems? I have never seen this before. I don't know if I should start over and used gparted or not. I'd like to solve any problems or potential issues before I spend any more time customizing.

---

### Post by oldfred on 2011-10-04
It is not a problem.

Drives have not used cylinder boundaries since hard drives exceeded 8GB and BIOS uses LBA or large block allocation. But all the partition tools thru Linux & XP installs still followed cylinders so partition tools never changed the error messages.

New partitioning tools with Vista and recent versions of gparted changed partition start from sector 63 to 2048. This improves performance with the new 4K drives & SSDs. Minor loss of a few sectors.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by Devan Dean on 2011-10-05
> Drives have not used cylinder boundaries since hard drives exceeded 8GB  and BIOS uses LBA or large block allocation. But all the partition tools  thru Linux & XP installs still followed cylinders so partition  tools never changed the error messages.

I think I better hurry and catch up!

Thanks for your help. The links you provided have good info that I am following up on. Thanks again.

---

### Post by crtlbreak on 2012-01-18
Another reason (as I have found today!) is that gparted was used to partition the disk when fdisk is called to check the status.
Just thought I would throw in my 10 pebbles worth ;-)

---

