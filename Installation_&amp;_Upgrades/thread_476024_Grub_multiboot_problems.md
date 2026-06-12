---
title: "Grub multiboot problems"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by Haree on 2007-06-16
Hi all,

I have some problem with grub. I have installed one Ubuntu distro (/dev/hdb1) and two Windows XP (/dev/hda1 and /dev/hdb5). Ubuntu boots fine, but if i want to boot one of the Windows it hangs with "Loading..." message. And if I put Windows XP installation CD into drive, don't press any key (so the installation program won't run), it normally boot the Windows (with windows selection menu).

fdisk -l
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylindry of 16065 * 512 = 8225280 bytes

Za&#345;ízení Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/hda4               1           1           0   10  OPUS
Partition 4 does not end on cylinder boundary.

Diskové oddíly jsou chybn&#283; se&#345;azeny
omitting empty partition (5)

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylindry of 16065 * 512 = 8225280 bytes

Za&#345;ízení Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       10199    81923436   83  Linux
/dev/hdb2           10200       10352     1228972+  82  Linux swap / Solaris
/dev/hdb3           10353       48641   307556392+   5  Rozší&#345;ený
/dev/hdb4           20551       48641   225640926    b  W95 FAT32
/dev/hdb5   *       10353       20550    81915372    7  HPFS/NTFS

```

menu.lst (shortened)
```

title		Windows XP Professional

# also don't work with rootnoverify	(hd0,0)
rootnoverify	(hd0,3)
savedefault
makeactive
chainloader	+1

title		Linux systems:
root

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hdb1 ro quiet resume=/dev/hdb2
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

```

I want to have all settings in grub and boot each system ONLY with selecting the item in grub (don't want any Windows selection menu). Please help

---

### Post by logos34 on 2007-06-16
Good luck trying to get Windows on hdb5 to boot...

As for Win XP on hda1, you can try adding this entry to menu.lst AFTER  the 'Automagic' section with your Ubuntu kernels:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

[B]title		Other operating systems:
root

title		 Windows XP
root		(hd1,0)
map	       (hd1) (hd0) 
map	       (hd0) (hd1)
savedefault
makeactive
chainloader	+1[/B]

Then make sure /boot/grub/device.map looks like this:

> (hd0) /dev/hdb
**(hd1) /dev/hda**

This assumes you are booting to grub on drive /dev/hdb.

The reason for putting windows after the automagic section is that it won't be kicked out of that section the next time there is a kernel update.  Also, the 'map' lines are necessary to fool windows into thinking that it's first in the BIOS hard disk boot priority (when in actuality it's second -- you're booting to grub on the 400BG drive.  It's the only way windows will boot).

---

### Post by Haree on 2007-06-17
Thank you for help, all system are working now, but Windows only with the M$ boot menu. Is it possible to f*** off the menu and use only the grub's one?

boot.ini on hda1
```

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP normal" 1

multi(0)disk(0)rdisk(1)partition(4)\WINDOWS="Windows XP games" /noexecute=optin /fastdetect

```

/boot/grub/device.map (changed)
```

(fd0)	/dev/fd0
(hd0)	/dev/hdb
(hd1)	/dev/hda
(hd2)	/dev/sda

```

/boot/grub/menu.lst (shortened, also changed)
```

title Windows XP
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
savedefault
makeactive
chainloader +1

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d2601ace-14ce-4676-9eba-c8df34e1f98e ro quiet resume=/dev/hda2
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d2601ace-14ce-4676-9eba-c8df34e1f98e ro single
initrd		/boot/initrd.img-2.6.20-16-generic

```

---

