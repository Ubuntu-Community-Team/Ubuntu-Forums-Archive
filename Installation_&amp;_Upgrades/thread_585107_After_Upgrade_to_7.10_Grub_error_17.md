---
title: "After Upgrade to 7.10 Grub error 17"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by miguel120 on 2007-10-21
My configuration:
2 IDE & 2 SATA Drives

1 IDE 40 GB  Windows XP
2 IDE 120 GB
3 SATA 120GB  Ubuntu 7.10
4 SATA 120GB

I am attaching fdisk -lu and menu.lst, Help will be appreciated.... Trying to move from Xp to Ubuntu.
Thanks,

miguel@Mojito:~$ sudo fdisk -lu
[sudo] password for miguel:

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef47ef47

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63    78156224    39078081    7  HPFS/NTFS

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a19b8e3

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd2   *       16065   234436544   117210240    5  Extended
/dev/hdd5           16135   234436544   117210205    7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a19b8ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *       48195   234436544   117194175    f  W95 Ext'd (LBA)
/dev/sda5           48258    79746659    39849201    b  W95 FAT32
/dev/sda6        79746723   234436544    77344911   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a19b8ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   228380039   114189988+  83  Linux
/dev/sdb2       228380040   234436544     3028252+   5  Extended
/dev/sdb5       228380103   234436544     3028221   82  Linux swap / Solaris
miguel@Mojito:~$ 

menu.lst

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c52427df-621b-4602-9bbe-2ce7978ec0d7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c52427df-621b-4602-9bbe-2ce7978ec0d7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c52427df-621b-4602-9bbe-2ce7978ec0d7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c52427df-621b-4602-9bbe-2ce7978ec0d7 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Pumalite on 2007-10-21
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
Maybe all you need to do is change the boot order of your hard drives.

---

