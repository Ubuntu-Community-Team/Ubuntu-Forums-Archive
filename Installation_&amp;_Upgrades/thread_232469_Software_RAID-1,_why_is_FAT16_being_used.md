---
title: "Software RAID-1, why is FAT16 being used?"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by voidPtr on 2006-08-08
I have installed Ubuntu creating two multi-disk devices (software RAID-1).  In the installer, I chose "physical raid volume" for all partitions before defining the MDs.  Installation was successful and both drives are recognized with mdadm tools.  What I _don't_ understand is why one partition (/dev/sdb1) shows up as FAT16. 

I am not the only one who has recognized this problem as I've found other forum members mentioning it without solution other than manually recreating the RAID array with the correct partition types.

This is causing issue when trying to install GRUB on /dev/sdb for redundancy.

fdisk -l:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18844   151364398+  fd  Linux raid autodetect
/dev/sda2           18845       19452     4883760   fd  Linux raid autodetect

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18844   151364398+   6  FAT16
/dev/sdb2           18845       19452     4883760   fd  Linux raid autodetect

Disk /dev/md0: 154.9 GB, 154997030912 bytes
2 heads, 4 sectors/track, 37841072 cylinders
Units = cylinders of 8 * 512 = 4096 bytes


Disk /dev/md1: 5000 MB, 5000855552 bytes
2 heads, 4 sectors/track, 1220912 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

---

