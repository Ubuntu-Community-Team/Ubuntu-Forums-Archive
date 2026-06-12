---
title: "2 distros missing from grub after install"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by jerry_murphy on 2014-10-05
Hi,
I installed lubuntu and now linux mint16 and kali linux are missing from grub. 
I updated grub 
> er@jer-desktop:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found unknown Linux distribution on /dev/sda6
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sda8
Found Windows 7 (loader) on /dev/sdb1
Found Linux Mint 15 Olivia (15) on /dev/sdb5
done

/dev/sdb is second older hard drive I don't use

fdisk does see the partitions however
> jer@jer-desktop:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000bf831

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    82051071    41024512    7  HPFS/NTFS/exFAT
/dev/sda2        82051072   408430591   163189760    7  HPFS/NTFS/exFAT
/dev/sda3       408430592   409454591      512000   83  Linux
/dev/sda4       409456638  1953523711   772033537    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       409456640   421810175     6176768   82  Linux swap / Solaris
/dev/sda6       476956672   536018943    29531136   83  Linux
/dev/sda7       536020992  1512194047   488086528    7  HPFS/NTFS/exFAT
/dev/sda8      1512196096  1953523711   220663808   83  Linux
/dev/sda9       421812224   476954623    27571200   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf234fab0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   117052975    58526456+   7  HPFS/NTFS/exFAT
/dev/sdb2       117053438   234440703    58693633    5  Extended
/dev/sdb5       117053440   226054143    54500352   83  Linux
/dev/sdb6       226056192   234440703     4192256   82  Linux swap / Solaris

Disk /dev/sdc: 1992 MB, 1992294400 bytes
6 heads, 5 sectors/track, 129706 cylinders, total 3891200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1a877630

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        3552     3891199     1943824    6  FAT16


I believe that sda 6 and sda9 are the 2 distos.
But how do I get grub to see them?
I've tried mounting them and updating grub no difference
Thanks
Jerry

---

### Post by yancek on 2014-10-05
The update-grub found a system on sda6, just lists it as unknown.  So you have Mint 15 on sdb5 and Mint 16 on sda9?  You could try running sudo os-prober and then update grub again.  Are you running this from Lubuntu?  Mount sda9 and take a look at the partition to see if the Mint 16 files you expect are there.

---

