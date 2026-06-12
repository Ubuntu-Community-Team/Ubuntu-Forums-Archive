---
title: "GRUB screwed up everything"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by TV-VCR on 2008-11-18
Since I installed GRUB, I can't boot into Windows.
> Starting up...
BOOTMGR is missing
Press CTrl+Alt+Del to restart

How do I fix this?
My menu.lst file:
> title		Windows Vista
root		(hd1,0)
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9fcdc342-f235-40e9-aa67-5cc7692b54ec
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9fcdc342-f235-40e9-aa67-5cc7692b54ec ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9fcdc342-f235-40e9-aa67-5cc7692b54ec
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9fcdc342-f235-40e9-aa67-5cc7692b54ec ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9fcdc342-f235-40e9-aa67-5cc7692b54ec
kernel		/boot/memtest86+.bin
quiet


Disk info:
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70841fad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     2000061    5  Extended
/dev/sda2   *         250        6474    50002312+  83  Linux
/dev/sda3            6475       60801   436381627+  83  Linux
/dev/sda5               1         249     2000029+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70841faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488383488    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64061985

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91202   732571648    7  HPFS/NTFS


---

### Post by louieb on 2008-11-18
try making widows think its on the 1st hard drive in the boot order.
```

title Vista
   map (hd0) (hd1)
   map (hd1) (hd0)
   rootnoverify (hd1,0)
   makeactive
   chainloader +1

```

---

