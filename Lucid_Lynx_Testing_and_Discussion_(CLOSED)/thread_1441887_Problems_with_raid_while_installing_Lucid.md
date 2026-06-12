---
title: "Problems with raid while installing Lucid"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Bultot on 2010-03-29
I was having Ubuntu Karmic till today. It was installed on a Raid1 partition with another Raid1 home partition:

/ = /dev/md0 = /dev/sda1 + /dev/sdb1
/home = /dev/md1 = /dev/sda2 + /dev/sdb2
/ntfs = /dev/sdc1

I wanted to install Lucid. No, I didn't want to upgrade so I went for a fresh install while keeping my /home folder. Downloaded the alternate installer and configured the Raid devices. While saving the Raid configuration, my system halted.
I rebooted my machine and wanted to try again. Then the filesystem on /dev/md1 wasn't recognized. I tried installing only on /dev/md0, leaving /dev/md1, but then the grub loader couldn't install.

I'd really like to know how to fix this. There is some valuebale data on /dev/md1. Can I check if it's still there?

Please guide me through this process.

This is the information I have at the moment:

Fdisk -l:
knoppix@Microknoppix:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007efc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6103    49022316   fd  Linux raid autodetect
/dev/sda2            6104       91201   683549685   83  Linux

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00083503

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6103    49022316   fd  Linux raid autodetect
/dev/sdb2            6104       91201   683549685   83  Linux

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x166abb0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13       30402   244093952    7  HPFS/NTFS

Disk /dev/md127: 50.2 GB, 50198740992 bytes
2 heads, 4 sectors/track, 12255552 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md127 doesn't contain a valid partition table

When  I assemle the /dev/md0 it doesn't contain a valid partition table or superblock...

---

### Post by Sef on 2010-03-29
Moved to Lucid.

---

