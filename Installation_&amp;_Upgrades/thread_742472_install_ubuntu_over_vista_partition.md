---
title: "install ubuntu over vista partition"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by mab1376 on 2008-04-01
im trying to install ubuntu 7.10 over my vista partition but the vista bootloader keeps overriding grub from my xp partition since thats the primary partition, how can i remove it without formatting?

fixboot and fixmbr from the recovery console do not work btw.

---

### Post by Pumalite on 2008-04-01
Boot your Live CD and, from the Terminal, post:
sudo fdisk -lu

---

### Post by mab1376 on 2008-04-03
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d6ad8de

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *       16065   490223474   245103705    f  W95 Ext'd (LBA)
/dev/hda5           16128   490223474   245103673+   7  HPFS/NTFS

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x77427742

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   502256159   251128048+   7  HPFS/NTFS
/dev/sda2       502256160   504248219      996030   82  Linux swap / Solaris
/dev/sda3       504248220   625137344    60444562+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000db6dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS

---

### Post by mab1376 on 2008-04-05
bump

---

### Post by Pumalite on 2008-04-05
Do you want to dual boot or Ubuntu solo?.

---

### Post by mab1376 on 2008-04-05
i want to dual boot with XP but the vista bootloader is still on my xp partition...

this might help ill try and get back you soon

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

---

### Post by Pumalite on 2008-04-06
If you haven-t done already, you might DBan your drive:[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted to make your partitions.

---

### Post by mab1376 on 2008-04-06
well the whole point of this thread is to find out how to do this without formatting my XP partition...

---

### Post by Pumalite on 2008-04-06
Which one is your Vista partition?

---

