---
title: "Mount NTFS file system in wine"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by JEEORRD on 2010-05-04
Trying to mount my NTFS file system (portable hard drive) so that is can be recognized by a program I have installed in wine (seagate manager).  I've tried to change the mount point for the drive to /home/.wine/c_drive but that doesn't seem to do the trick, and messing around with the fstab file just results in error messages when I try to mount/unmount the drive.

Anybody know who to change the mount point properly?  /dev/sbd1 is my partition.

Either that or does anyone know how to configure wine so that it will find my drive?  I've tried adding an e: drive to the drives tab and mapped it to \media\Simons' Seagate (partition label), but that doesn't seem to do the trick either.

---

### Post by JEEORRD on 2010-05-09
OK so this isn't an issue anymore, I just decided to forget trying to use the software that came with the drive through wine and starting using Back In Time instead.

---

