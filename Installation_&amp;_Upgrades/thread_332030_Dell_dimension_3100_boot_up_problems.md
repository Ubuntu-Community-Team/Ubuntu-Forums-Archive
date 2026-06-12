---
title: "Dell dimension 3100 boot up problems"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by manij on 2007-01-05
I'm trying to run Kubuntu on my dell dimension 3100.

I install it on a ide hard drive attached as a slave in CDROM ide port/connection.

The installation goes w/o any problem.

however when I try to reboot, the kubuntu installation is not being recognized. This is the cae even when I adjust the boot sequence in the bios to be first one to boot from the ide drive.

the problem doesn't go away even if I disconnect my SATA drive. I just the response back indicating there is no boot drive.

Here is what sudo fdisk command outputs!

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 4813 38660391 83 Linux
/dev/hdb2 4814 4998 1486012+ 5 Extended
/dev/hdb5 4814 4998 1485981 82 Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 4 32098+ de Dell Utility
/dev/sda2 * 5 14179 113860687+ 7 HPFS/NTFS
/dev/sda3 14181 19022 38893365 7 HPFS/NTFS
/dev/sda4 19023 19452 3453975 db CP/M / CTOS / ...

As you can see the kubuntu installation is in the smaller HD.

What am I doing wrong.

Thanks
Mani

---

