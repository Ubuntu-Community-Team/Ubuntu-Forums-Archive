---
title: "Can't access HDD with Windows 10 on it"
date: 2015-11-07
forum: Installation &amp; Upgrades
---

### Post by lallkopf on 2015-11-07
I'm new with Linux and need some support since I couldn't find the right support for my issue via Yahoo search (Google blocked in China ).
I newly installed the Mint distribution on another HDD. In parallel I have another HDD with Windows 10 with some partitions installed. Both work fine separately. I now would like to mount the Windows HDD, but it always comes to this error:

Error mounting /dev/sda9 at /media/tommy/Filme: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda9" "/media/tommy/Filme"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda9': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

I shut down Windows 10 correctly (twice) and yet the error stays. fdisk brings the following result:

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 Köpfe, 63 Sektoren/Spur, 182401 Zylinder, zusammen 2930277168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x0fcab92a


   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   204795903   102294528    7  HPFS/NTFS/exFAT
/dev/sda3       204795904  2930272064  1362738080+   5  Erweiterte
/dev/sda5       204796683   409593239   102398278+   7  HPFS/NTFS/exFAT
/dev/sda6       409593303   614389859   102398278+   7  HPFS/NTFS/exFAT
/dev/sda7       614389923  1638389024   511999551    7  HPFS/NTFS/exFAT
/dev/sda8      1638389088  1843185644   102398278+   7  HPFS/NTFS/exFAT
/dev/sda9      1843185708  2930272064   543543178+   7  HPFS/NTFS/exFAT


Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 Köpfe, 63 Sektoren/Spur, 38913 Zylinder, zusammen 625142448 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x0001d57f


   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *        2048    39063551    19530752   83  Linux
/dev/sdb2        39065598   625141759   293038081    5  Erweiterte
/dev/sdb5        39065600    48828415     4881408   82  Linux Swap / Solaris
/dev/sdb6        48830464   625141759   288155648   83  Linux

Can someone help me to access the NTFS partitions?

Beside this problem I have, most likely, another smaller problem. I installed the proprietary driver for my AMD graphic card. It shows only Chinese language. Any idea how to change this?

---

### Post by lallkopf on 2015-11-08
Solution found for mounting. I used PYSDM and voila it worked.

---

### Post by Bucky Ball on 2015-11-08
Welcome. Thanks for sharing and please see first link in my signature to mark the thread as solved and please post support questions regarding Mint in the [***Mint*** sub-section]("http://ubuntuforums.org/forumdisplay.php?f=453"). You'd increase your chances of support by posting on the very active Linux Mint forums as well/instead. Although Mint is based on Ubuntu, it is not officially supported in the main areas here. :)

---

