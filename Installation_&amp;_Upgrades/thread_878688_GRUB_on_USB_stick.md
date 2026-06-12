---
title: "GRUB on USB stick"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by 1095 on 2008-08-03
i All,

I have troubles installing grub on USB stick.

My setup

fdisk
```

# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9e09b62

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda45e8de

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf13d1d21

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bdc6797

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd2               1       60801   488384001   83  Linux
/dev/sdd4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d428d42

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         609     4891761    7  HPFS/NTFS
/dev/sde2             610        1219     4899825   83  Linux
/dev/sde3            1220        1283      514080   82  Linux swap / Solaris
/dev/sde4            1284       60801   478078335    f  W95 Ext'd (LBA)
/dev/sde5            1284        2589    10490413+  83  Linux
/dev/sde6            2590        2615      208813+  83  Linux
/dev/sde7            2616       60801   467379013+   b  W95 FAT32

Disk /dev/sdf: 2029 MB, 2029518848 bytes
255 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         233     1871541    b  W95 FAT32
/dev/sdf2             234         246      104422+  83  Linux

```

Linux
```

# grep sde /proc/mounts 
/dev/sde5 / ext3 rw,data=ordered 0 0
/dev/sde6 /boot ext2 rw 0 0

```

grub.conf
```

# cat /boot/grub/grub.conf 

default 0
timeout 30

title Linux 2.6.25-r6 17.07.2008 - 18:54
root (hd0,5)
kernel (hd0,5)/linux-200807171854-2.6.25-r6 root=/dev/sde5 video=0x31B
real_root=/dev/sdd3

title=Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

```

Because /dev/sd[abc] have no patition table I modified /boot/grub/device.map:
```

# cat /boot/grub/device.map 
(hd0)   /dev/sde
(hd1)   /dev/sdf

```

grub works well from /dev/sde

_Then I tried to put /boot  on USB stick (dev/sdf)._

I did exactly the following:

Copy all files from /boot to /mnt/sdf2. 
Remount /dev/sdf2 as /boot
Modify grub.conf 
```

$ cat /boot/grub/device.map
(hd0)   /dev/sdf
(hd1)   /dev/sde

```

Modify /boot/grub/grub.conf
```


default 0
timeout 30

title Linux 2.6.25-r6 17.07.2008 - 18:54
root (hd0,1)
kernel (hd0,1)/linux-200807171854-2.6.25-r6 root=/dev/sde5 video=0x31B

title=Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

```

update /etc/mtab (As I booted from LiveCD)
```

 grep -v rootfs /proc/mounts  > /etc/mtab

```

install grub:
```

$grub-install /dev/sdf
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sdf
(hd1)   /dev/sde

```

After reboot I'm getting black screen. Looks like stage1 cannot be found on USB.

Any idea where the problem can be?

Thanks.

---

### Post by dileepm on 2008-08-04
Try the procedure [http://www.scribd.com/doc/4090276/Installing-Ubuntu-In-Pen-Drive](http://www.scribd.com/doc/4090276/Installing-Ubuntu-In-Pen-Drive)

---

