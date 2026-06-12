---
title: "upgrade 7.10 to 8.04 : IDE &amp; SATA : device names/order"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by ramora_t on 2008-09-05
Hi all,

Since I upgraded from 7.10 to 8.04, I have 2 weird problems with my IDE & SATA disks.
First IDE devices are not labeled /dev/hdX anymore but /dev/sdX. Well it's OK I've just corrected my /etc/fstab. I've been told that it's "normal".

Secondly the device names change on every boot : the /dev/sdc becomes /dev/sdb and so on.. I have to boot twice to "correct" the problem.

This is the order I expect :

Disque /dev/sda: 250.0 Go, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0x000cd11e

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1         127     1020096   82  Linux swap / Solaris
/dev/sda2             128        6606    52042567+  83  Linux

Disque /dev/sdb: 163.9 Go, 163928604672 octets
255 heads, 63 sectors/track, 19929 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0x43569730

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1               1        6080    48837568+  83  Linux
/dev/sdb2   *        6081        7296     9767520    7  HPFS/NTFS
/dev/sdb3            7297       16407    73184107+   f  W95 Etendu (LBA)
/dev/sdb4           16408       19929    28290465   83  Linux
/dev/sdb5            7297       16407    73184076    c  W95 FAT32 (LBA)

Disque /dev/sdc: 80.0 Go, 80026361856 octets
255 heads, 63 sectors/track, 9729 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0x1aa642b1

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdc1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/sdc2            1217        9729    68380672+   f  W95 Etendu (LBA)
/dev/sdc5            1217        9729    68380641    b  W95 FAT32

Any idea ?

---

### Post by Vivaldi Gloria on 2008-09-05
Why is the device change a problem? Do you use uuids in fstab?

---

### Post by zdude on 2008-09-05
I had the same problem and I was using a /home partition that was encryted on the second drive. Big problem. I ended up using UUID everywhere there is a /dev/sdX (menu.lst, fstab, crypttab, etc) . This so far has worked, although a pain in a$$ to setup but it does work.

---

### Post by ramora_t on 2008-09-10
Hi,

Thank you for your replies.
No Vivaldi Gloria I don't use uuid. Just old style device names :
If sdb becomes sdc or whatever .. it puts a mess and the system won't boot properly.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1       /home           ext3    defaults        0       2
/dev/sda2       /externe           ext3    defaults        0       2
/dev/sdc1       /media/C        ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0 
      1
/dev/sdc5       /media/D        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb2       /media/F        ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0 
      1
/dev/sdb5       /media/H        vfat    defaults,utf8,umask=007,gid=46 0       1

---

### Post by Vivaldi Gloria on 2008-09-10
> **ramora_t said:**
> Hi,

Thank you for your replies.
No Vivaldi Gloria I don't use uuid. Just old style device names :
If sdb becomes sdc or whatever .. it puts a mess and the system won't boot properly.


You need to learn the uuids of partitions and use them in fstab. For example a line in my fstab looks like this:

```
UUID=425a54d6-7033-4114-b0e6-868257abd717 /mnt/misc      ext3    relatime        0       2
```

So you put the uuids as "UUID=???" at the beginning of the line. To learn the uuids use the commands:

```
ls /dev/disk/* -lah
sudo blkid
```

Here is an fstab guide: [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

