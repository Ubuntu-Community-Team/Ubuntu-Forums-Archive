---
title: "realign disk partitions on new sdd"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by RogerTa on 2013-05-06
Hi all,

Summary:
Copying an old hdd to a new ssd results in misaligned partitions.  Is there a way to fix this during the copy or after the copy?

Full version:

I am running ubuntu 10.04.4 LTS:

```
$ uname -a   
Linux sodium 2.6.32-46-generic #108-Ubuntu SMP Thu Apr 11 15:56:25 UTC 2013 x86_64 GNU/Linux

$ cat  /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
```


The main disk was a Hitachi Travelstar 7K200 hdd, which I upgraded to an ssd.  I did not want to reinstall the OS or s/w packages, so I cloned the disk using the command:

```
dd if=/dev/sda of=/dev/sdb
```

I then took the original hdd out and put the ssd in its place.  The machine boots just fine with the side effect of being much faster :-)  However, with I run fdisk I get warnings about misalignment of sector boundaries:

```
$ sudo fdisk -l -u

Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x158fa71c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   240187814   120093876    7  HPFS/NTFS
Partition 1 does not start on physical sector boundary.
/dev/sda2       240187815   312576704    36194445    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       240187878   309508289    34660206   83  Linux
Partition 5 does not start on physical sector boundary.
/dev/sda6       309508353   312576704     1534176   82  Linux swap / Solaris
Partition 6 does not start on physical sector boundary.

```

I did some research and found that newer disk really like partitions to be 4K aligned, whereas older disk only need 512 byte alignment.  See [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

Is there anyway to realign the partitions without erasing them?

Alternatively, is there anyway to copy the original hdd to the ssd using dd (or some other tool) that can realign as the copy is made?

Thanks!

---

### Post by darkod on 2013-05-07
I'm not aware of a way to realign now, but you might find something on google. The problem is that realigning would mean moving the partitions which is much more dangerous then simply redoing it again.

But this time don't use dd that uses sector by sector copy, and includes empty sectors too. Simply copy the files from live mode. But that has two drawbacks:
1. Keep your ubuntu cd at hand, you will have to reinstall grub2 to the MBR.
2. You will have to change the UUIDs of the partition in /etc/fstab after you copy it.

If you want to give that a shot, and need more details, just ask. Note that while copying you need to keep ownership and permissions. The command for that is: cp -ax. The -ax options keep ownership and permissions.

I think you could realign with parted, but as I said, I also think it's risky because that means moving partitions. Besides, if you have no space left at the end of the disk, it might not have where to move partitions.

Redoing the partitions will also allow you to use all of the space. Right not the ssd is "cut" to the size of the old disk, that's how dd does it.

PS. You could also try cloning from the old to the new directly with clonezilla. But make the new partitions on the new disk first of course. They need to be equal or bigger size compared to the source partitions. And the newly created ones will be aligned, most partitioning tools like Gparted will do that by default.

---

### Post by RogerTa on 2013-05-10
Thanks for all the tips darkod.  I've decided to just re-install a clean build of 12.04 LTS on the ssd.  Turns out it was not so bad to setup my environment again.

---

### Post by darkod on 2013-05-11
Good choice. It often takes less time then we expect.

---

