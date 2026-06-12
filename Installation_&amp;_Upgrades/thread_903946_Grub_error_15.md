---
title: "Grub error 15"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by theshadowwithanmp5n on 2008-08-28
I have installed ubuntu onto my USB (8 Gigs of memory).
I know the bootloader works, because it shows all the options when I boot into GRUB.
However, whenever I click one of the optinos, whether it's windows, ubuntu (hard drive), or the pen drive linux (ubuntu as well), I get GRUB Error 15 Cannot find file (or something very close to that).
When I boot without the USB, everything works, but the option for the Pen drive doesn't show up (i know that's supposed to happen, i'm not that stupid). I've been trying to do this on my own for a week, and the problems used to be much worse, but I managed to fix them without much research.
This problem is a bitch though.

Any help would be appreciated.

---

### Post by caljohnsmith on 2008-08-28
Sounds like it is probably a simple case of not having the correct (hdX,Y) entries for your operating systems specified in your Grub's /boot/grub/menu.lst. With your flash drive connected, please post the following: 
```
sudo fdisk -lu

```
And tell us which partitions correspond to which operating system if you can. Also post the /boot/grub/menu.lst that's on your flash drive.

---

### Post by theshadowwithanmp5n on 2008-08-29
> 
Disk /dev/sda: 120.0 GB, 120034123776 bytes ###This is Windows Partition
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5fec5fec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       64259       32098+  de  Dell Utility
/dev/sda2   *       64260   234436544   117186142+   7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes ###This is the Desktop's Linux Partition
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c702c70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    76903154    38451546   83  Linux
/dev/sdb2        76903155    80292869     1694857+   5  Extended
/dev/sdb5        76903218    80292869     1694826   82  Linux swap / Solaris

Disk /dev/sdc: 8029 MB, 8029470208 bytes ###This is the USB, it's active for booting.
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00010f2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    14908319     7454128+  83  Linux
/dev/sdc2        14908320    15679439      385560    5  Extended
/dev/sdc5        14908383    15679439      385528+  82  Linux swap / Solaris

/dev/sdc: /boot/grub/menu.lst
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=15dd3e56-0166-4ecd-9ade-a68c189618ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=15dd3e56-0166-4ecd-9ade-a68c189618ef ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a641735f-7b99-4b92-9d9f-6ded4550142d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a641735f-7b99-4b92-9d9f-6ded4550142d ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=a641735f-7b99-4b92-9d9f-6ded4550142d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=a641735f-7b99-4b92-9d9f-6ded4550142d ro single 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


That's the info, and thanks for taking the time to help me.
One quick note, I can't get MemTest 86+ to work either.

---

### Post by theshadowwithanmp5n on 2008-08-29
i couldn't see it before, but it compressed all the spaces, so it may be a bit confusing.

---

### Post by caljohnsmith on 2008-08-29
OK, looks like it might be easy to fix your problem. For all the Ubuntu entries at the beginning of your menu.lst:
```
title Ubuntu 8.04, kernel 2.6.24-16-generic
root [COLOR="Blue"](hd2,0)[/COLOR]
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=15dd3e56-0166-4ecd-9ade-a68c189618ef ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root [COLOR="Blue"](hd2,0)[/COLOR]
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=15dd3e56-0166-4ecd-9ade-a68c189618ef ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root [COLOR="Blue"](hd2,0)[/COLOR]
kernel /boot/memtest86+.bin
quiet
```
I assume those are for your flash drive, true? Because the other Ubuntu entries that come after that reference your sdb HDD, which is not your flash drive. If that is true, then change all the (hd2,0) references above to (hd0,0). That should work, unless maybe the UUIDs are wrong too, but not likely. Try that first, and if that works, then we can correct your Windows and Ubuntu (on /dev/sdb) entries after that.

---

### Post by theshadowwithanmp5n on 2008-08-29
IT WORKED!!!
the bootloader found linux on the flash drive.
one problem now, my account that I set up at installation couldn't load.
i checked the teletypewriters (tty1-tty6) and they were fine, but the graphics part couldn't load up.
either that, or it was taking too long.
i left it alone after five minutes waiting, took a shower, and came back and it was still trying to load.

---

