---
title: "Weird Grub Problem"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by gibbylinks on 2006-09-27
Hi,

   I have a dual boot system Win XP Pro & Linux

I recently zapped my Dapper installation and installed Edgy. Grub totally screwed up and it took a bit of messing around with it to get to boot into either system. 

My problem is that while I can boot straight into Linux now, when I pick XP it can't find the partition !! But get this, if I edit the menu change it from what it says (hd0,0) to say (hd1,0) let it refuse then edit it back to (hd0,0) it boots !!!

I have 3 hard drives - 2 SATA & 1 PATA

fdisk -lu gives me the following output.

Disk /dev/hdh: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1   *          63   115121789    57560863+   7  HPFS/NTFS
/dev/hdh2       115121790   117226304     1052257+   b  W95 FAT32

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   115314569    57657253+   7  HPFS/NTFS
/dev/sda2   *   115314570   154223999    19454715   83  Linux
/dev/sda3       154224000   156296384     1036192+  82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   320159384   160079661    7  HPFS/NTFS

with 

/dev/sda1 WinXP
/dev/sda2 linux root
/dev/sda3 linux swap partition

/dev/sdb1 Music

/dev/hdh1 Docs etc
/dev/hdh2 E-Mail & Browser bookmarks (Shared between XP & Linux)


and my grub menu.lst is

title		Ubuntu, kernel 2.6.17-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-9-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-9-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-9-generic (single-user mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-9-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-9-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Can anyone see anything ?

Thanks

---

### Post by gibbylinks on 2006-09-27
Ok I lied,

I've just done an update which has added a new kernel to my grub menu. I've just had to edit the menu item and use (hd1,0) to boot into Win XP - It seems to keep changing on me ??

---

### Post by geezerone on 2006-09-27
Have you carried out a 'fixmbr' with the Automated Recovery Console in XP (via CD or installed on harddisk)? This would wipe the Grub boot record so you can boot into XP (hopefully) and then you could install 'Edgy Eft' again (creates grub record) or just install Grub into mbr? Just an idea but maybe someone with more 'Ubuntu' experience may come up with another answer? :-k

---

### Post by gibbylinks on 2006-09-27
I can boot into XP, It's just a question of finding the right numbers each time (hd0,0) (hd1,0) !!

What I want is to find a way of getting the thing to "stick" so I don't have to keep editing the grub menu

Thanks

---

### Post by geezerone on 2006-09-27
I appreciate that you have a weird problem but part of my suggestion was that wiping 'Grub' with 'fixmbr' command and reinstall of Grub/Edgy may clear it up in the quickest time. :)

Will need to check my Linux Grub to see how I am configured.

---

