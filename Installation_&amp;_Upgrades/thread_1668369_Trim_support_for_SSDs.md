---
title: "Trim support for SSDs"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by lorenzone92 on 2011-01-16
Hello! :)

I have an OCZ Vertex II 60GB SSD with Win7 installed. I'd like to move to Ubuntu.
The only thing I need to know before proceed is: does Ubuntu 10.10 support SSDs correctly (with trim also)? Are they "aligned" properly or are there issues?

Thanks in advance,
Lorenzo

---

### Post by lorenzone92 on 2011-01-16
Up...?

---

### Post by efflandt on 2011-01-17
Yes TRIM is supported for ext4 in Maverick if you use the **discard** option in /etc/fstab, and **noatime** can avoid writing file access times (when just reading files).  I have plenty of RAM, so I have no swap and used tmpfs for /tmp.  I am actually using ext4 with journal disabled, and have not had any drive issues with Intel SSD (currently running Natty development).

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e70810eb-379d-4f9f-9087-54c2f1cd96f9 /    ext4    **noatime**,**discard**,errors=remount-ro 0       1
tmpfs        /tmp        tmpfs    nodev,nosuid    0    0
```I don't really know how important partition alignment is or how files are aligned beyond the beginning of a partition (whether Linux even pays attention to cylinders).  The default since 10.04 is to align partitions to MB boundaries instead of cylinder boundaries.  But I had seen something about setting 512 KB cylinders by using fdisk to set 32 heads and 32 sectors with first partition at cylinder 2, so that is what I did.

```
**sudo fdisk -l /dev/sdb**

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
32 heads, 32 sectors/track, 152638 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a571

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2      152638    78150144   83  Linux

**sudo fdisk -lu /dev/sdb**

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
32 heads, 32 sectors/track, 152638 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a571

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1024   156301311    78150144   83  Linux
```Note: If you change any partitions on the SSD with gparted, it will change your drive to 255 heads, 63 sectors/track, regardless of what they were.

---

