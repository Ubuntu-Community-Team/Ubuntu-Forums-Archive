---
title: "Grub problems after upgrade to 10.10"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by evil_iggy on 2010-10-21
Hi,

I recently upgraged to 10.10, and it all worked fine until grub choaked after restart. I know this is a common story now. I searched the forums and booted from a live CD, uninstalled grub, then reinstalled it, but grub still fails to load. However, for some odd reason, if I go into the boot menu (I have a dell) and select my second hard drive, grub starts correctly.

I am dual booting Win7 and Ubuntu.

I've tried update-grub and I get the following:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/System Reserved/boot
Boot: No such file or directory
```here is the output from fdisk -l

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       17320   139017216    7  HPFS/NTFS
/dev/sda3           17646       30394   102398976    6  FAT16
/dev/sda4           17321       17645     2610562+   b  W95 FAT32
```Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2fa4e565

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         128     1024000    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sdb2             129       60801   487355872+   5  Extended
/dev/sdb5             129       59672   478287148+  83  Linux
/dev/sdb6           59673       60801     9068661   82  Linux swap / Solaris
```
here is blkid
   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       17320   139017216    7  HPFS/NTFS
/dev/sda3           17646       30394   102398976    6  FAT16
/dev/sda4           17321       17645     2610562+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2fa4e565

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         128     1024000    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sdb2             129       60801   487355872+   5  Extended
/dev/sdb5             129       59672   478287148+  83  Linux
/dev/sdb6           59673       60801     9068661   82  Linux swap / Solaris
```Any help is much appreciated

---

