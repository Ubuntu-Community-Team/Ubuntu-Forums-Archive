---
title: "grub error 17, fdisk doesn't show partition i need to fix device.map"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by spip on 2011-06-21
Hello,

I tried installing ubuntu 11.04 on a system that already had ubuntu 10.10 + windows XP as a dual boot. The exisiting setup was two drives (which I'll call Small and Big), with Small being master and having two partitions, one for linux and for for XP. Grub is the boot loader.

I chose the "erase previous ubuntu" install option. Installation failed due to some unknown error (but I do think think Small might be failing). When I boot, I now get Grub error 17.

This ubuntu forum thread seemed to be it ([http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)), in particular mbwardle's answer ([http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9)).

I booted using the Install CD. To determine which partition should be listed first in my device.map, I ran 'fdisk -l'. It listed Big as /dev/sda and Small as /dev/sdb. However, it only showed one partition for /dev/sdb, which was /dev/sdb1, and that is the NTFS partition. I can't see the ext3 (or whatever it was I used back when I installed ubuntu 9 a long time ago and upgraded all the way to 10), so I can't really mount what I need in order to change (or even check device.map.

Any idea what could be wrong at this stage? Could it be that the ubuntu installation erased the partition and failed before properly recreating the partition? Could it be anything simpler, something I'm doing wrong?

[edit] Here is the output of 'fdisk -l':

/dev/sdb is the drive we should boot from, and it is supposed to contain two partitions, and the one I need is not listed...

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd827047a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1     1938018   976761040+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f9c6f9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30514   245103673+   7  HPFS/NTFS



Thanks,
Spip

---

