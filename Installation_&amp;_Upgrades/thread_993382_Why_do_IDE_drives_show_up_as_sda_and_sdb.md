---
title: "Why do IDE drives show up as sda and sdb?"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by h20Boodle on 2008-11-25
I've got two IDE drives in my machine, and they're showing up as /dev/sda and /dev/sdb instead of /dev/hda and /dev/hdc as I would have expected. Can anyone explain why this would be? 

Thanks for the help.

Ubuntu 8.04.

fdisk -l:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c2fba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14311   114953076   83  Linux
/dev/sda2           14312       14593     2265165    5  Extended
/dev/sda5           14312       14593     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003335e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25496   204796588+  83  Linux
/dev/sdb2           25497       38913   107772052+  83  Linux


menu.lst:
default		0
timeout		3
hiddenmenu

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=74a73227-e424-4bd9-8693-728c7878a122 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic

fstab:
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=74a73227-e424-4bd9-8693-728c7878a122 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=78de36e8-1ab5-46bb-9671-42dbbf78623b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc2        /media/d2  auto    rw,user,noauto  0   
quiet

---

### Post by logos34 on 2008-11-25
the reason they show up as 'sda' is because ubuntu has swtiched to the [libata scsi storage driver]("https://blueprints.launchpad.net/ubuntu/+spec/libata-for-all-ata-disks") for all disks

---

