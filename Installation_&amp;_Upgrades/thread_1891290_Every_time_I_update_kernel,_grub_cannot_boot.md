---
title: "Every time I update kernel, grub cannot boot"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by zachlac on 2011-12-05
Every time I do an update to the linux kernel, GRUB fails to boot.  To  fix this problem, every time I have to boot from a rescue CD, do lots of  crazy mount commands to get a chroot-ed environment set up, then to a  dpkg-reconfigure grub.

How can I fix this so that GRUB updates itself correctly when a new kernel is installed?

Machine specifics:
Linux 2.6.35-std210-amd64 #2 SMP Fri Apr 1 21:13:29 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.3 LTS

It's set up with RAID 1, so here is the disk info:

# fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   fd  Linux raid autodetect
/dev/sda2           28450       30394    15623212+  82  Linux swap / Solaris
/dev/sda3              32       28449   228267585   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdb: 251.1 GB, 251059544064 bytes
255 heads, 63 sectors/track, 30522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24c60f47

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          31      248976   fd  Linux raid autodetect
/dev/sdb2           28450       30394    15623212+  82  Linux swap / Solaris
/dev/sdb3              32       28449   228267585   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/md127: 233.7 GB, 233745940480 bytes
2 heads, 4 sectors/track, 57066880 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md127 doesn't contain a valid partition table

Disk /dev/md126: 254 MB, 254869504 bytes
2 heads, 4 sectors/track, 62224 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md126 doesn't contain a valid partition table

---

### Post by 2F4U on 2011-12-05
Thats the same thread as here:

[http://ubuntuforums.org/showthread.php?t=1888966](http://ubuntuforums.org/showthread.php?t=1888966)

---

