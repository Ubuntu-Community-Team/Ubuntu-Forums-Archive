---
title: "used hard drive install trouble"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by jason82 on 2010-01-26
So I was going to try to move my ubuntu install to a bigger hard drive (currently on a 40 gb id) i had an extra 500 gb sata laying around i install it and tryed to format and i get 

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sdc1 from /media/new movie storage
 and this when i try to unmount 

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sdc1 from /media/new movie storage


why is it mounted from /media/new movie storage,  im lost 

im running ubuntu 9.10 64 bit 

also just in case you need it here is the output of fdisk -l 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28717ab0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1604    12884098+   7  HPFS/NTFS
/dev/sda2            1605       38913   299684542+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75bb6990

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x240b515b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488383488    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30bdb4d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sde: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfaa543ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        4660    37431418+  83  Linux
/dev/sde2            4661        4865     1646662+   5  Extended
/dev/sde5            4661        4865     1646631   82  Linux swap / Solaris
jason@jason-desktop5:~$

---

### Post by jason82 on 2010-01-29
any ideas

---

### Post by darkod on 2010-01-29
You could try booting with the cd, Try Ubuntu option, open Gparted and format the 500GB like that if that's what you want. Of course, this will wipe out all data from the disk!
And how did you plan to move ubuntu, to create ext4 partitions on the 500GB disk and then image your ubuntu and restore on the new disk?

---

### Post by jason82 on 2010-01-30
ill have to try that any reason this is happening and for the swap yeah something like that i found several ways to do it and you make it sound so easy:smile:

---

