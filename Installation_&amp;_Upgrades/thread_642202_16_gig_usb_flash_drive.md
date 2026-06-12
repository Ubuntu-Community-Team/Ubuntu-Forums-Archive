---
title: "16 gig usb flash drive"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by donvan on 2007-12-16
I just purchased a 16 gig generic USB flash drive from eBay.  I have already install UBUNTU 7.10 on a 1 gig USB drive and had hoped to use the new one in the same way.  However when using the command fdisk -l to get the drive identifier I got the following:

Disk /dev/sdb: 16.7 GB, 16777216512 bytes
64 heads, 32 sectors/track, 16000 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x730b5e03

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      911769     1816261   926200368+  8e  Linux LVM
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?           5           5           0   65  Novell Netware 386
Partition 2 does not end on cylinder boundary.
/dev/sdb4   ?      680965      680975       10668+  45  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
When I try to unmount : the partitions I get the following:

umount: /dev/sdb1 is not mounted (according to mtab)

What do I do to continue? If I use a third party program "Partition Magic" under XP will it screw up the drive geometry for UBUNTU and for XP?

---

### Post by dixonp on 2007-12-18
Whatever the previous owner did with this USB flash drive, it simply appears to not be partitionned correctly (its MBR contains random data). Just recreate a new, empty partition table with this command that writes NUL bytes to the first 512-byte sector (**warning: only run it if you are sure you don't care about the existing data on /dev/sdb**):

# dd if=/dev/zero bs=512 count=1 of=/dev/sdb

Then create the partition table(s) with fdisk or other partitioning tools:

# fdisk /dev/sdb
  (then "n" for "create New partition", etc)

---

