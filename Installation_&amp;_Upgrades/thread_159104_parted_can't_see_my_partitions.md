---
title: "parted can't see my partitions"
date: 2006-04-12
forum: Installation &amp; Upgrades
---

### Post by dbd on 2006-04-12
Hi,
Was trying to install Ubunu again, since loads of stuff has been going wrong in the last few days, so I thought I'd do a fresh install, just keep my home partition.
Anyway, the installer won't list the partitions for one of my hard drives.

When I run parted on that drive and try the print command it says:
> Error: Unable to satisfy all constraints on the partition.

And cfdisk says:
> FATAL ERROR: Bad logical partition 5:

But Fdisk -l on that drive seems fine, it says:
> Disk /dev/hda: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8161     4113112+   c  W95 FAT32 (LBA)
/dev/hda2            8176      158816    75922561    5  Extended
/dev/hda3           16459       24688     4147888+  83  Linux
/dev/hda5           24689       49101    12304120+   b  W95 FAT32
/dev/hda6           49102       73534    12314200+   b  W95 FAT32
/dev/hda7           73535       98004    12332848+   b  W95 FAT32
/dev/hda8           98005      122484    12337888+   b  W95 FAT32
/dev/hda9          122485      158816    18311296+   b  W95 FAT32
/dev/hda10           8177       16458     4174097+   b  W95 FAT32

Partition table entries are not in disk order


I'm not really up for deleting all the partions and repartitioning the drive, Although that is an option, I suppose I am due a backup of my data. 
Any ideas? Preferably ones that don't involve risking my data.

Thanks

---

### Post by dbd on 2006-04-13
Problem solved, kinda.

I just installed to hdb (the hard drive that parted can see), and then played around with mounting after it was installed so that /usr used a partition from hda. (I had a 2.2 GB partition spare on hdb, so enough for install, but not enough to be install everything else I wanted).

So if you have a similar problem, then don't worry. Even if a hard drive's partitions are not visible on install, they may still be useable after install if fdisk is ok with them.

---

