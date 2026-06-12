---
title: "windows partition died"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by terrymcintyreatyahoo.com on 2006-10-02
I installed Ubuntu 6.06 LTS on an HP a1250n. When I tried booting to Windows, got HP's magickal recovery partition, which offered to wipe the real Windows partition with a virgin install of Windows ... a scary prospect!

Output of fdisk -l :

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1046     8399128+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1047       17324   130753035    7  HPFS/NTFS
/dev/sda3           17325       30047   102197497+  83  Linux
/dev/sda4           30048       30401     2843505    5  Extended
/dev/sda5           30048       30401     2843473+  82  Linux swap/Solaris

Attempted to mount via:

mount -t ntfs /dev/sda2 /media/windows
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg output is:

[17182680.600000] NTFS-fs warning (device sda2): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17182680.600000] NTFS-fs error (device sda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17182680.600000] NTFS-fs error (device sda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17182680.600000] NTFS-fs error (device sda2): ntfs_fill_super(): Not an NTFS volume.

My first priority is to recover the data on /dev/sda2 -- if I can boot as Windows, all the better.

I modified the menu.lst entry and attempted to boot, and it failed:

title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Any advice would be greatly appreciated. Thanks!

---

### Post by randell6564 on 2006-10-02
[S-ATA devices]("http://linuxmafia.com/faq/Hardware/sata.html") and Linux

---

