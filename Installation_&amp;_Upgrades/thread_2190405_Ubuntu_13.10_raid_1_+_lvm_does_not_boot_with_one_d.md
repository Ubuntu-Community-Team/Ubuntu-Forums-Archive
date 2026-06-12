---
title: "Ubuntu 13.10 raid 1 + lvm does not boot with one disk detached"
date: 2013-11-27
forum: Installation &amp; Upgrades
---

### Post by kakulacis2 on 2013-11-27
Hi!

I'v installed ubuntu server 13.10, configured two disks for raid 1 at installation and also configured lvm at installation. System is booting up correctly, mirror is synced, but when i disconnect any of hard drives system won't boot anymore and is stuck on emply black screen. What could be the cause of that.

```

root@lserver:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00037d76

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1953523711   976760832   fd  Linux raid autodetect

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004d511

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   156301311    78149632   fd  Linux raid autodetect

Disk /dev/md0: 80.0 GB, 79957983232 bytes
2 heads, 4 sectors/track, 19520992 cylinders, total 156167936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/mapper/GROUP1-swap: 3955 MB, 3955228672 bytes
255 heads, 63 sectors/track, 480 cylinders, total 7725056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/GROUP1-swap doesn't contain a valid partition table

Disk /dev/mapper/GROUP1-data: 76.0 GB, 76000788480 bytes
255 heads, 63 sectors/track, 9239 cylinders, total 148439040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/GROUP1-data doesn't contain a valid partition table
root@lserver:~# pico /boot/grub/grub.cfg

```

```

root@lserver:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/GROUP1-data /               ext4    errors=remount-ro 0       1
/dev/mapper/GROUP1-swap none            swap    sw              0       0


```

---

### Post by kakulacis2 on 2013-11-28
Just did a workaround, created separate partitions for boot and raid 1 without lvm on those partitions, created raid 1 and lvm on non boot partitions, this way it's working.

---

