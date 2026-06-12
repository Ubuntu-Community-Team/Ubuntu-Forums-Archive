---
title: "Installation of Ubuntu disables Windows XP"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by Elementary31 on 2008-03-11
When i try to install Ubuntu and use dual boot with windows xp everything works fine when installinh ubuntu but when i try to select windows xp from the list of os's when restarting my computer, windows xp acts like it wants to load but then it immediately stops and the computer restarts.  I have tried using the ubuntu partition, and using gparted to partition it. Now i have windows xp installed on a partition (NTFS) and i also have a separate FAT32 partition which i created using the software that came with my harddrive and i was wondering how would i go about installing ubuntu on the FAT32 partition without it disabling windows xp like it has been doin

---

### Post by froy02 on 2008-03-11
Most probably you resized the windows partition when you first installed Ubuntu and windows saw that the partition was resized and will try to chkdsk the windows partition.  The reboot is normal for that time and it usually take a while for windows to finish the disk check.
You can install Ubuntu on the fat32 partition but it would change that to ext3 type since Ubuntu uses ext3.  There should not be a problem installing Ubuntu on that partition.

---

