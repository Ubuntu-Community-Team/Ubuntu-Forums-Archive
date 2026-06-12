---
title: "Big problem with fstab on installng a new hard drive"
date: 2005-09-18
forum: Installation &amp; Upgrades
---

### Post by Doctoxic on 2005-09-18
Hi All

Situation is as follows:

I have had Ubuntu up and running fine, however i haven't used it for a week or so and in the meantime i have made 2 hardware changes:
1) Installed extra SATA drive
2) Swopped the 2x512 Geil RAM into the other slots.

I (foolishly?) did not change anything in Ubuntu prior to doing this - i must confess that i thought it would auto detect like in windows.

Now when i try to boot Ubuntu i get these messages:

pivot_root: no such file or directory
/sbin/init: 428 cannot open dev/console no such file
Kernal panic - not syncing : attempted to kill init


Now i gather the probelm is something to do with the new hard drive corrupting the 'fsab' file but i am not sure what the fstab should look like.

Here's some more info:

it was the 250gig SATA that was just added)
i am pretty sure that prior to install the original SATA was 'sda0'
the follwoing info was taken after booting from the live CD
the fstab file looks very empty

based on the fdisk info can anyone tell me exactly what my fstab file should look like?

FDISK -L
======================================================
Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/sda1 2 484521 244198080 f W95 Ext'd (LBA)
/dev/sda5 2 484521 244198048+ 7 HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 7649 61440561 7 HPFS/NTFS
/dev/sdb2 7650 7655 48195 83 Linux
/dev/sdb3 7656 7764 875542+ 82 Linux swap / Solaris
/dev/sdb4 7765 24321 132994102+ 83 Linux

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 5004 40194598+ c W95 FAT32 (LBA)
root@ubuntu:/home/ubuntu #
=======================================================

Now for the FSTAB - but i don't think this looks right? Or is it the FSTAB just from the live CD? it was in /etc - should i be looking somewhere else?

======================================================
/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb3 swap swap defaults 0 0
=======================================================


many thanks

Doc

---

