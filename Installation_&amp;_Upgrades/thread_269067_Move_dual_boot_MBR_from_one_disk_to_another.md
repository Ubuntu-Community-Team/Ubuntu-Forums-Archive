---
title: "Move dual boot MBR from one disk to another"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by cemptor on 2006-10-01
I installed Windows XP on a machine with two drives - 1 ATA and 1 SATA and then installed 32 bit Dapper with GRUB. Installed both OSs on the SATA drive (sda). Now I want to use the ATA drive (hda) only for backups. But it seems to contain the MBR

My fdisk -lu shows:

[COLOR="Orange"][I]Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2          498015   205294634   102398310    5  Extended
/dev/hda3       285314400   321669494    18177547+  83  Linux
/dev/hda5          498078   205294634   102398278+  8e  Linux LVM

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      498014      248976   83  Linux
/dev/sda2          498015     4401809     1951897+  82  Linux swap / Solaris
/dev/sda3         4401810   566467964   281033077+   5  Extended
/dev/sda4   *   566467965   586950839    10241437+   7  HPFS/NTFS
/dev/sda5         4401873    66476969    31037548+  83  Linux
/dev/sda6        66477033    97723394    15623181    b  W95 FAT32
/dev/sda7        97723458   566467964   234372253+  8e  Linux LVM[/I][/COLOR]

I think my ATA drive (hda) was jumpered as master as well as my SATA (sda) when I installed Windows XP and GRUB. So I can only boot with hda as the first drive set on my BIOS. It leads me to think the MBR is on my hda

My /boot/grub/menu.lst (on sda1) is:

[I][COLOR="Orange"]title           Ubuntu, kernel 2.6.15-27-386
root            (hd1,0)
kernel          /vmlinuz-2.6.15-27-386 root=/dev/sda5 ro quiet splash
initrd          /initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd1,0)
kernel          /vmlinuz-2.6.15-27-386 root=/dev/sda5 ro single
initrd          /initrd.img-2.6.15-27-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title           Microsoft Windows XP Home Edition
rootnoverify            (hd1,3)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1[/COLOR][/I]

Why does my system need hda as the first drive to boot? How can I correct this? 
I don't want to use hda for regular use, but only as a backup. Don't need the current partitions on it.

Thanks!

---

### Post by Ocxic on 2006-10-01
this same exact things has happend to me, and even now, I'm unable to find a fix for this problem. it seems to be a bug in GRUB i think maybe, the way it sees the disks, or the way the bios deals with them. for now i guess we just have to deal, no biggie anyways if your never gonna take the drive out.

---

