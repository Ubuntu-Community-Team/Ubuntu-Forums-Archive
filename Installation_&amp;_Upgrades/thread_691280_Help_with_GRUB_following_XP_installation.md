---
title: "Help with GRUB following XP installation"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Trapper Dave on 2008-02-08
I'm just wondering if anyone can help.

I initially installed Vista on my machine and then created a partition on the hard drive and installed Ubuntu on it. I then let GRUB deal with the booting.

I then needed to install XP onto the machine as well, but as I was running low on space on the first hard disk I created a partition on a second hard disk. After some playing about and resetting the Ubuntu partition as the boot one, when GRUB loads up and asks me what partition to load; I run into trouble. 

Ubuntu will load fine from it, but the option that once loaded Vista now loads XP and the one that is meant to load XP doesn't work.

Ubuntu is located in sad2.

Vista is located in sda1.

XP is located in sdb5.

My current menu.lst is:

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ecb21c16-3f3e-4180-bbdf-83e25b9032c2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ecb21c16-3f3e-4180-bbdf-83e25b9032c2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd1,4)
savedefault
makeactive
chainloader	+1

```

Does anyone have any ideas or suggestions as to how I might be able to fix this?

---

### Post by Trapper Dave on 2008-02-08
Both are SATA hard disks. What I don't understand is how GRUB is pointing to Vista but booting XP.

Also here is my fdisk information.

[CODE]

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22702   182350749    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           22703       30074    59215590   83  Linux
/dev/sda3           30075       30394     2570400    5  Extended
/dev/sda5           30075       30394     2570368+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6cc1585a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       58844   472655872    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           58845       60800    15711570    5  Extended
/dev/sdb5           58845       60800    15711538+   7  HPFS/NTFS
[\CODE]

---

