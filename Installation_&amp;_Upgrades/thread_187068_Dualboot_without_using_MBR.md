---
title: "Dualboot without using MBR"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by binsh on 2006-06-02
Hey,

I have the following setup:

/dev/hda 120GB   - Storage
/dev/sda 74GB Sata - WindowsXP
/dev/sdb 74GB Sata - Ubuntu 6.06
      
      /sdb1  /boot
      /sdb2  /swap
      /sdb3  /home
      /sdb5  /


I used the alternate cd so I could choose were to install grub which I installed to  /dev/sdb1.

Booted livecd and used dd to copy boot image and added it to my NTLDR.

Upon reboot I get:

GRUB

and menu doesn't come up.

Other distro as well have given me this problem since I moved from having all   PATA to SATA. Lilo works without problems in this configuration.

I would really prefer not to use sda MBR if possible, any help on this would be great, thanks.

---

### Post by binsh on 2006-06-03
Wanted to add some detailed  information:

root@ubuntu:/mnt/boot_tmp/grub# fdisk -lu

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   145195469    72597703+   7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      192779       96358+  83  Linux
/dev/sdb2          192780     4096574     1951897+  82  Linux swap / Solaris
/dev/sdb3         4096575    86124464    41013945   83  Linux
/dev/sdb4        86124465   145211534    29543535    5  Extended
/dev/sdb5        86124528   125194544    19535008+  83  Linux
/dev/sdb6       125194608   145211534    10008463+  83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   155653784    77826861    7  HPFS/NTFS
/dev/hda2       155653785   156296384      321300    e  W95 FAT16 (LBA)

root@ubuntu:/mnt/boot_tmp/grub# cat device.map
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb

root@ubuntu:/mnt/boot_tmp/grub# cat menu.lst

title           Ubuntu, kernel 2.6.15-23-386
root            (hd2,0)
kernel          /vmlinuz-2.6.15-23-386 root=/dev/sdb5 ro quiet splash
initrd          /initrd.img-2.6.15-23-386
savedefault
boot

---

