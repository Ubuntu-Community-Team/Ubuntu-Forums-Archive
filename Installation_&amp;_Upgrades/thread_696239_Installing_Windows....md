---
title: "Installing Windows..."
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by Niloc on 2008-02-13
I have a wonderful Feisty system but I want to install Win2K or XP in a 65gig partition and dual boot it with Linux.
fDisk -l gives me :

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+   b  W95 FAT32
/dev/sda2            1217        9726    68356575    7  HPFS/NTFS
/dev/sda3            9727       10212     3903795   82  Linux swap / Solaris
/dev/sda4           10213       16291    48829567+   5  Extended
/dev/sda5           10213       11428     9767488+  83  Linux
/dev/sda6           11429       16291    39062016   83  Linux

You can see I have already made sda2 an NTFS partition with gParted but what is the next step? How do I get either of the Windows disks to boot and install into the partition?

Thanks.
Colin

---

### Post by Pumalite on 2008-02-13
Is better to install Windows first in sda1. It's also better to give it the whole hard drive and then shrink the partition to install Ubuntu. I'm not a Windows user, but I think Windows will refuse to install in sda2.

---

