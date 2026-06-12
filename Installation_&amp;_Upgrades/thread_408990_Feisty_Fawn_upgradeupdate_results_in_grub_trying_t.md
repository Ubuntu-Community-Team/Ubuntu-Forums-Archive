---
title: "Feisty Fawn upgrade/update results in grub trying to boot from the wrong partition"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by DarrylShields on 2007-04-14
Hi,

Just thought I'd let you know that after upgrading from Edgy to Feisty and then again after today's updates, I got a "Error 17: Cannot mount selected partition" message.

In both cases the root partition in grub had changed and the "root=" parameter changed to using UUID and was pointing at the first partition on the hard disk (a Dell partition).

After doing the following, it was working again:

1.  Booted from the Feisty Fawn CD-ROM

2.  Opened a terrminal window and became root

> sudo su - root

3.  Listed by hard disk partitions

#> fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        3830    30716280    7  HPFS/NTFS
/dev/sda3            3831       19065   122375137+   f  W95 Ext'd (LBA)
/dev/sda4           19066       19457     3148740   db  CP/M / CTOS / ...
/dev/sda5   *        3831        7495    29439049+  83  Linux
/dev/sda6            7496        7655     1285168+  82  Linux swap / Solaris
/dev/sda7           18805       19065     2096451   dd  Unknown
/dev/sda8            7656       18804    89554311   83  Linux

Partition table entries are not in disk order

4.  Saw that the boot partitions had an asterisk and that /dev/sda5 was my Linux boot partition (sda2 was Windows)

5.  Created a mount point and mounted the hard disk

#> mkdir /mnt/hdd
#> mount /dev/sda5 /mnt/hdd

6.  Changed to the hard disk and updated the grub menu.lst file

#> cd /mnt/hdd/boot/grub
#> vi menu.lst 

From the partition list above I knew I needed /dev/sda5 and that the number used in grub is one less that the partition, because it starts counting from zero, rather than one.  So I changed (hd0,6) to (hd0,4) and rebooted, but had the same problem.  

Second time I got rid of the UUID and specified the partition directly (root =/dev/sda5, rather than root=UUID=07D7-0118)

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

After rebooting, everything was working fine again.

8.  Out of curiosity I checked the UUID to see what is was pointing at

> sudo vol_id -u /dev/sda5
4f7850c1-85f8-4629-80e3-a831bfb8ffce
> sudo vol_id -u /dev/sda1
07D7-0118

I hope this can filter into the upgrade process so it doesn't occur when Feisty is released and/or is helpful for others with a similar problem.

---

