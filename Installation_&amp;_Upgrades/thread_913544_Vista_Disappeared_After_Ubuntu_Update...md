---
title: "Vista Disappeared After Ubuntu Update.."
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by Resin on 2008-09-07
Hey everyone,

I recently did a (large) update to my copy of ubuntu after everything downloaded and installed, Vista no longer appeared on my boot menu :(

I know it didnt delete the partition as fdisk reveals its still there...

I'm juts not sure how to enter Vista's details back into GRUB so I cant boot back into Vista.

Here is the results from fdisk -l

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       19131   143109116    7  HPFS/NTFS
/dev/sda4           19131       19458     2621440    f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a562e90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18055   145023996    7  HPFS/NTFS
/dev/sdb2           18056       19457    11261565    5  Extended
/dev/sdb5           18056       19392    10739421   83  Linux
/dev/sdb6           19393       19457      522081   82  Linux swap / Solaris


And GRUB's menu.lst currently looks like this:
> 
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6753f9ec-2c2f-4cc6-8ecf-e5ba0266348a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6753f9ec-2c2f-4cc6-8ecf-e5ba0266348a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6753f9ec-2c2f-4cc6-8ecf-e5ba0266348a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6753f9ec-2c2f-4cc6-8ecf-e5ba0266348a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

If anyone could help so I can add the vista details back into GRUB, that would be much appreciated.

---

### Post by ad_267 on 2008-09-07
Based on my menu.lst you probably need to add something like this at the bottom:

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Microsoft Windows Vista
root            (hd0,2)
savedefault
makeactive
chainloader     +1


```

---

### Post by Resin on 2008-09-07
> **ad_267 said:**
> Based on my menu.lst you probably need to add something like this at the bottom:

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Microsoft Windows Vista
root            (hd0,2)
savedefault
makeactive
chainloader     +1


```

Hey I tried the above to the menu.lst file except I had in (hd0,0) assuming that the vista partition would be a the start of the disk.  It appeared in the menu, but nothing happened when it was selected...

any other ideas?

---

### Post by ad_267 on 2008-09-08
I think it should be hd(0,2) because from your fdisk output I thought this was the bootable vista partition because it has a star:
/dev/sda3 * 1315 19131 143109116 7 HPFS/NTFS

hd(0,0) is that dell utility partition.

---

