---
title: "can't mount internal NTFS"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by mr tim esquire on 2007-04-09
When i double click on the drive in Computer i get:-
error: device /dev/hdc1 is not removable

error: could not execute pmount

I tried installing ntfs-3g but still not working
im trying to get hdc1 working:-

tim@desk:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/hda2            2433        2693     2096482+  82  Linux swap / Solaris
/dev/hda3            2694        4865    17446590   83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       36483   293049666    c  W95 FAT32 (LBA)

Thanks for the help!
Tim :)

---

### Post by sam81 on 2007-04-09
You need to add an entry in the file /etc/fstab, something along the lines of the following

/dev/hdc1       /media/hdc1     ntfs    auto,users,rw,exec,umask=000   0       0

upon reboot it should be mounted always automatically. Otherwise you can mount it from the command line, but you need root privileges for that.

---

