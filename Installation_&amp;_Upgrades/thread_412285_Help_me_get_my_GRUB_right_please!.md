---
title: "Help me get my GRUB right please!"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by herbster on 2007-04-17
I have one SATA in 2 partitions, a 50gb with XP and a 250gb with Vista, and one SATA with Ubuntu (partitioned for root, home and an extra). I am trying to get it to triple-boot, and I have done it before I reinstalled Edgy so I'd like to get it back.

Here's my fdisk -l output:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            1276        1785     4096575   82  Linux swap / Solaris
/dev/sda3            1786        4334    20474842+  83  Linux
/dev/sda4            4335       38913   277755817+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7012    56323858+   7  HPFS/NTFS
/dev/sdb2            7013       38912   256236750    f  W95 Ext'd (LBA)
/dev/sdb5            7013       38912   256236718+   7  HPFS/NTFS
```

Here's the relevant part of my grub menu.lst:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd1,1)
savedefault
makeactive
chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Vista/Longhorn
root        (hd1,2)
map        (hd1,2) (hd1,1)
map        (hd1,1) (hd1,2)
savedefault
makeactive
chainloader    +1
```

I added the XP and Vista entries myself from memory but of course they aren't working right, as the XP entry boots the Vista bootloader allowing me to choose Vista or XP, but if I choose XP from that it reboots :confused:

Help!

---

### Post by confused57 on 2007-04-17
You might try this, I'm not familiar with Vista, but you can give it a shot:

```
title        Microsoft Windows XP Home Edition
root        (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Vista/Longhorn
root        (hd1,4)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader    +1
```

You "may" not need the mapping lines for Vista.

Added:  Here's an idea I've never tried, but it might work:
```
title        Microsoft Windows XP Home Edition
root        (hd1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1
```

this entry "might" boot to the mbr of your Window's drive, allowing you to choose XP or Vista...of course, if the first 2 entries work, they would be easier.

---

### Post by herbster on 2007-04-22
confused57,

Thanks so much, that worked perfectly man! :) :D

---

