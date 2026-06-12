---
title: "GRUB XP problem"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by mcgregorj on 2007-01-28
Here's my problem.  Installed Edgy to dual boot w/ XP.  Everything was fine.  Had some useless partitions on my HD (Dell utility drive and Norton Ghost drive) that I wanted to get rid of to use the space.  Dell util drive was hda1.  I got rid of these 2 drives, had to fix menu.lst and boot.ini, but everything was a-ok for both OS's.  

The problems arose when I used all the extra space to create a new fat32 drive, which gparted decided to name hda1.  After this, XP wouldn't start (got the restart when I select it in GRUB).  Ubuntu is working fine.

Here's my menu.lst and fdisk -l output.  Thanks in advance for any help!

**GRUB menu.lst:**

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
boot

title		Microsoft Windows XP 
rootnoverify (hd0,1)
savedefault
makeactive
chainloader	+1

**FDISK -L OUTPUT:**

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *           1        5057    40620321    7  HPFS/NTFS
/dev/hda3            5058        5855     6409935    5  Extended
/dev/hda5            5058        5120      506016   82  Linux swap / Solaris
/dev/hda6            5121        5855     5903856   83  Linux

---

### Post by mcgregorj on 2007-01-28
Oh, I deleted the hda1 partition (which was at the end of the drive).

---

