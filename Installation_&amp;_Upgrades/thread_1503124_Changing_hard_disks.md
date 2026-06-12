---
title: "Changing hard disks"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by mosaic2s on 2010-06-06
I am using ubuntu 10.04 on SATA hard disk and other OS on second hard disk. the grub boot loader is installed on the MBR of the other OS.
If I remove ubuntu 10.04, the error shows on booting - no such partition.
I probably need to edit the grub entry to rejig partition info.
Pl advise where to look?

If I remove OTHER OS hard disk, same error shows up. can I install boot loader again on the ubuntu hard disk?

---

### Post by darkod on 2010-06-06
Boot ubuntu, run in terminal:

sudo fdisk -l (small L)

and post the results.

You should install grub2 on the MBR of the ubuntu disk. When you remove the ubuntu disk, grub2 on the MBR of the other disk has no config files to read and that's why it reports the error.

---

### Post by mosaic2s on 2010-06-06
results are posted below.
i need to install ubuntu hard disk on another system of similar config.
plus i need to keep the other os running with only one disk - is that possible by editing the grub written on the mbr of the other os?


ubuntu@ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00017727

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x099f099e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9345    75062272   83  Linux
/dev/sdb3            9346        9729     3084480   82  Linux swap / Solaris

---

### Post by darkod on 2010-06-06
OK, as you can see, you probably have windows on disk /dev/sda and ubuntu on disk /dev/sdb. However, during install grub2 from ubuntu was installed on the MBR of disk /dev/sda, the windows disk.

You need to install grub2 to /dev/sdb and windows bootloader to /dev/sda.

Installing grub2 to /dev/sdb is easy, just boot ubuntu and in terminal do:

sudo grub-install /dev/sdb

That will sort it out. Unplug the ubuntu disk, and boot with your windows dvd to repair the MBR of /dev/sda. If you need instructions, look here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If the windows dvd is giving you problems, you can install generic MBR which will do the same job from the ubuntu cd in live mode with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give. That should make windows boot without the ubuntu disk.

When you have both disks connected, you have to select in BIOS which one you want to be primary for boot.

---

### Post by mosaic2s on 2010-06-06
I did exactly that. it works like a charm.
thanks. it has made the whole thing so easy. and i can update and keep my ubuntu working instead of reformatting etc etc.

---

