---
title: "dd not working for me!?!"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by volksman on 2006-07-29
Hey All!

I have an issue with dd I can't really figure out.  Hopefully someone can point me in the right direction.  here's the scoop:

I have a 40G IDE drive with Ubuntu installed on it.  In the same machine I have a 200G SATA drive (sdb) which has my old NTFS partitions from my windows load (which I'm happy to say I have yet to touch since I installed Ubuntu).

Now I installed a new 120G SATA drive (sda) in the system and would like to move the Ubuntu install from /dev/hda to /dev/sda (the new 120G drive).

Here is my fdisk results:

Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14346   115234213+  83  Linux
/dev/sda2           14347       14593     1984027+   5  Extended
/dev/sda5           14347       14593     1983996   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sdb2            1913       24792   183783600    7  HPFS/NTFS

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4665    37471581   83  Linux
/dev/hda2            4666        4866     1614532+   5  Extended
/dev/hda5            4666        4866     1614501   82  Linux swap / Solaris


Keeping things simple I want an exact duplicate of the existing drive just with the added space.  So the partition table for /dev/sda is the way I want it.  Now I want to clone /dev/hda1 to /dev/sda1, dd says this:

dd: writing to `/dev/sda1': No space left on device
1034817+0 records in
1034816+0 records out
529825792 bytes (530 MB) copied, 19.935 seconds, 26.6 MB/s


After copying 530 Megs it claims sda1 is full?  How does that make sense?  What am I doing wrong?

---

