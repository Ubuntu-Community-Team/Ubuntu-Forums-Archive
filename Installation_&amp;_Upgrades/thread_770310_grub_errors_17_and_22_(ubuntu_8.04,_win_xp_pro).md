---
title: "grub errors 17 and 22 (ubuntu 8.04, win xp pro)"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by alterlatz on 2008-04-27
i'm new with ubuntu wanted to try it out!

i installed ubuntu on my second HD (IDE) and win xp was on the first drive (SATA).

during bootup i had to manually choose the ide drive so grub showed up. otherwise grub wouldn't start and windows would boot up.

my guess was, grub didn't install on the SATA drive so i installed it on both drives with "grub-install /dev/sda". now grub always started but i got those errors.
"Error 17 : Cannot mount selected partition" was the message for all linux boot options.
"Error 22: No such partition" for my windows installation.

the only method to boot was with a ubuntu live cd and choosing the boot loader from the cd and every OS worked.

i tryed to make windows boot properly with the windows recovery console and used the commands fixmbr and fixboot. but unfortunately i made things worse. now nothing boots. only errors 17 and 22.

reinstallation of ubuntu (the windows way :) ) didn't help. reinstalling windows works properly until the first reboot when windows runs into grub.

```
ubuntu@ubuntu:/media$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01090109

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    f  W95 Ext'd (LBA)
/dev/sda2   *        3285       24321   168979671    7  HPFS/NTFS
/dev/sda5               1        1216     9767425+  83  Linux
/dev/sda6            1217        1338      979933+  82  Linux swap / Solaris
/dev/sda7            1339        3284    15631213+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00470047

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sdb2            1306       60800   477893587+   f  W95 Ext'd (LBA)
/dev/sdb5            1306        1697     3148708+   7  HPFS/NTFS
/dev/sdb6            1698        8224    52428096    7  HPFS/NTFS
/dev/sdb7            8225       34332   209712478+   7  HPFS/NTFS
/dev/sdb8           34333       60800   212604178+   7  HPFS/NTFS
```

my fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=670a9161-dc61-4b77-8e62-7a2182e69db3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=d10a47e4-95c9-4ee7-9dac-5794f77a90b6 /home           ext3    relatime        0       2
# /dev/sda7
UUID=339d630a-b421-47cf-99eb-3aff79024115 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```
grub menu.lst
```
title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=670a9161-dc61-4b77-8e62-7a2182e69db3 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=670a9161-dc61-4b77-8e62-7a2182e69db3 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

if additional system info is needed, just tell me.

i'm looking forward to your replies, thank you!
:popcorn:

---

### Post by Pumalite on 2008-04-27
Use your first drive (SATA) to install both OS and leave the IDE for storage or a separate /home

---

