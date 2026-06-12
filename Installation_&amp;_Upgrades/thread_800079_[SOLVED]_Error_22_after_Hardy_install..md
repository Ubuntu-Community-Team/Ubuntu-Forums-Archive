---
title: "[SOLVED] Error 22 after Hardy install."
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by xmastree on 2008-05-19
Major problems here... :(

My current setup was:
Primary master (hda) 40GB split 20/20 with XP and Ubuntu 7.04
Primary Slave (hdb) 80GB fat32 data
SATA (sda) 80GB fat32 data.

The Ubuntu installation was borked, so I decided to install 8.04 over it. I went to manual partitioning, removed the ext3 partition and told it to make one there and use it.
It created sdb6.

For some reason my disks were no longer hda & hdb but the 40GB was now sdb, with 80GB disks at sda and sdc. I suspect the SATA is sda, but I can't tell for sure.

Anyway, upon reboot I get grub error 22.

Current status is I've booted from the live Hardy disc, and am looking at /boot/grub/menu.lst (from the ext3 partition at sdb6), which looks ok:

```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=83f88561-fe3b-4c0b-8d88-f3f0cd751e0c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=83f88561-fe3b-4c0b-8d88-f3f0cd751e0c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

And here's the output of fdisk -l

```

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc9e3d40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc892c892

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2433    19543041    7  HPFS/NTFS
/dev/sdb3            2434        4865    19535040    5  Extended
/dev/sdb5            4763        4865      827316   82  Linux swap / Solaris
/dev/sdb6            2434        4762    18707629+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c32e617

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sdc5               2        9729    78140128+   b  W95 FAT32


```

So, what's the next step?

---

### Post by xmastree on 2008-05-19
Well, I appear to have fixed it, but what a pain in the wossname.

First, I followed [these instructions]("http://ubuntuforums.org/showthread.php?t=224351"), which brought up the grub menu as defined in menu.lst
But that wasn't the end of it.
I started messing around with menu.lst figuring that I couldn't make it much worse.
Changed **root		(hd1,5)** to **root		(hd0,5)** and ubuntu would now boot, but not XP.
So, I changed XP's root to 0,0 then removed those 'map' lines and all seems to be well again.


So it's fixed, *but what was Hardy thinking of to mess it up so badly?*

---

