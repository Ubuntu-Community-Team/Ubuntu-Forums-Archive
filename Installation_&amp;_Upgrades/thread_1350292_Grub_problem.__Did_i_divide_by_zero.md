---
title: "Grub problem.  Did i divide by zero?"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by bugflash on 2009-12-09
Hi...  I had a working dualboot installation with Winxp and ubuntu 9.10 on the only hd in my system (sda) and i installed partition magic in windows to make room for an other linux installation. I resized the windows partition and booted from a live usb stick and installed the other linux distro and got a new grub. The new grub had added the posts from the old one but when i tried to boot my old buntu i got this error: grub error 15: file not found. The last installation (kubuntu) and winxp boots okay. What to do?

Here's my old ubuntu menu.lst and fstab:

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        00f43141-49ff-4bf9-997c-ee2cc50d0d51
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=00f43141-49ff-4bf9-997c-ee2cc50d0d51 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        00f43141-49ff-4bf9-997c-ee2cc50d0d51
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=00f43141-49ff-4bf9-997c-ee2cc50d0d51 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        00f43141-49ff-4bf9-997c-ee2cc50d0d51
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=00f43141-49ff-4bf9-997c-ee2cc50d0d51 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        00f43141-49ff-4bf9-997c-ee2cc50d0d51
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=00f43141-49ff-4bf9-997c-ee2cc50d0d51 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, memtest86+
uuid        00f43141-49ff-4bf9-997c-ee2cc50d0d51
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


Fstab:

proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=00f43141-49ff-4bf9-997c-ee2cc50d0d51 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0200f07b-9421-4d6d-a411-3a8a288a22cb none            swap    sw              0       0


-------------------------------------------------------------------------------------------------------------------------


Here's the new ones

## ## End Default Options ##

splashimage=2d057c48-f8d4-43a9-8ef5-8abf106c1494/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.29.4
uuid        2d057c48-f8d4-43a9-8ef5-8abf106c1494
kernel        /boot/vmlinuz-2.6.29.4 root=UUID=2d057c48-f8d4-43a9-8ef5-8abf106c1494 ro quiet splash 
initrd        /boot/initrd.img-2.6.29.4
quiet

title        Ubuntu 8.10, kernel 2.6.29.4 (recovery mode)
uuid        2d057c48-f8d4-43a9-8ef5-8abf106c1494
kernel        /boot/vmlinuz-2.6.29.4 root=UUID=2d057c48-f8d4-43a9-8ef5-8abf106c1494 ro  single
initrd        /boot/initrd.img-2.6.29.4

title        Ubuntu 8.10, memtest86+
uuid        2d057c48-f8d4-43a9-8ef5-8abf106c1494
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-16-generic root=00f43141-49ff-4bf9-997c-ee2cc50d0d51 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sda6)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=00f43141-49ff-4bf9-997c-ee2cc50d0d51 ro single 
initrd        /boot/initrd.img-2.6.31-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=00f43141-49ff-4bf9-997c-ee2cc50d0d51 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=00f43141-49ff-4bf9-997c-ee2cc50d0d51 ro single 
initrd        /boot/initrd.img-2.6.31-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.10, memtest86+ (on /dev/sda6)
root        (hd0,5)
kernel        /boot/memtest86+.bin  
savedefault
boot


And fstab:

proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=2d057c48-f8d4-43a9-8ef5-8abf106c1494 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=02f07b94-214d-6da4-113a-8a288a22cb1f none            swap    sw              0       0

I would be very pleased if someone can help me...  (my potentially new gilfriend is trapped in the ubuntu installation)

---

### Post by rahilm on 2009-12-09
Check if (hd0,5) is your ubuntu. I can see conflicting partition numbers here and there

boot into kubuntu or via live cd, go to terminal and run
sudo fdisk -l

post the output here

---

### Post by bugflash on 2009-12-09
Her it is


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006631a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2189    17583111    7  HPFS/NTFS
/dev/sda2            2190       30401   226612890    f  W95 Ext'd (LBA)
/dev/sda5            3303       28799   204804621    7  HPFS/NTFS
/dev/sda6           28800       30327    12273628+  83  Linux
/dev/sda7           30328       30401      594373+  82  Linux swap / Solaris
/dev/sda8            2190        3302     8940109+  83  Linux

Partition table entries are not in disk order

---

### Post by darkod on 2009-12-09
It looks normal. How come you had menu.lst for the "old" install when it's 9.10 that comes with grub2? Was that an upgrade from 9.04?
Also, when adding another linux I guess it's better to leave you old grub running the show. You will just make entry for the new linux in it (or it will do it automatically).

I would boot with 9.10 cd, select Try Ubuntu and install grub2 on the MBR. It finds other installations automatically, maybe that will do the trick.

---

### Post by rahilm on 2009-12-09
and I heard from upgrade users that grub legacy has problems with ext4 system. Although i couldn't test it.
The reason i asked to post fdisk -l was that if you look at the entry for 9.10 recovery mode, it points to the partition (hd0,6) so I thought that might be the error of file not found

---

### Post by darkod on 2009-12-09
> **rahilm said:**
> 
The reason i asked to post fdisk -l was that if you look at the entry for 9.10 recovery mode, it points to the partition (hd0,6) so I thought that might be the error of file not found

Indeed, I didn't notice that. They all say /dev/sda6 but only that entry uses (hd0,6) which would be correct for grub2, the rest use (hd0,5) which would be correct for grub1 on the other hand.
I think you have a major confusion in there.

---

