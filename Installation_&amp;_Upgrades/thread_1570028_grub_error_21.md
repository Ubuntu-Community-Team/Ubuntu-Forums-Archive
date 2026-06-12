---
title: "grub error 21"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by jonmark1985 on 2010-09-07
I'm having error 21 problems with grub.

I'm using a HP pavilion laptop with windows Vista.  I was using Ubuntu 8.04 on a 2 gig thumbdrive.  I was toying around with a 4 gig thumb drive as well.  I tried to install Ubuntu 8.04 to the 4 gig stick.  In the process I assume this changed the MBR.

Now upon boot with the 4 gig thumb drive removed I get a grub error 21.  I don't have the windows disc to restore the windows mbr, so I assume I have to install grub to the laptop hard drive.

When I try to install grub to SDA1 using a live cd I recieve a message saying...

not found or not a block device

thanks for your help

---

### Post by jonmark1985 on 2010-09-07
this is what i get when trying to install grub

root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x475d475c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22796   183108838+   7  HPFS/NTFS
/dev/sda2           22797       24321    12249562+   7  HPFS/NTFS

Disk /dev/sdb: 2021 MB, 2021654016 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x000e6a2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1010     1972499    c  W95 FAT32 (LBA)

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b6c78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         460     3694918+  83  Linux
/dev/sdc2             461         489      232942+   5  Extended
/dev/sdc5             461         489      232911   82  Linux swap / Solaris
root@ubuntu:/home/ubuntu# grub-install /dev/sda1
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/home/ubuntu#

---

