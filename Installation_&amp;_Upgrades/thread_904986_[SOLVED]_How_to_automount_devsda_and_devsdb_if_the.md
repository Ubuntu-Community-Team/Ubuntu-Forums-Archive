---
title: "[SOLVED] How to automount /dev/sda and /dev/sdb if they  keep switching after reboot?"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by bmwman on 2008-08-29
I have my HTPC with 300gb IDE and 500gb SATA drives. Ubuntu is installed on the 300gb drive which also has 3gb swap partition. The SATA drive has 470gb partition which has most my movies, music, etc. and 30gb unpartitioned if I ever decide to load XP. The problem is every time I reboot the IDE and SATA drives keep switching, once one is /dev/sda and the other one is /dev/sdb, next time it's the other way around.


How can I automount /dev/sda2 or /dev/sdb2 whichever is my SATA partition to /home/backend/Media if they  keep switching after reboot?

Thanks

---

### Post by iaculallad on 2008-08-29
> **bmwman said:**
> I have my HTPC with 300gb IDE and 500gb SATA drives. Ubuntu is installed on the 300gb drive which also has 3gb swap partition. The SATA drive has 470gb partition which has most my movies, music, etc. and 30gb unpartitioned if I ever decide to load XP. The problem is every time I reboot the IDE and SATA drives keep switching, once one is /dev/sda and the other one is /dev/sdb, next time it's the other way around.


How can I automount /dev/sda2 or /dev/sdb2 whichever is my SATA partition to /home/backend/Media if they  keep switching after reboot?

Thanks

Try posting whatever displays when you issue the 3 terminal commands below:

```
sudo blkid
sudo fdisk -l
cat /etc/fstab
```

---

### Post by bmwman on 2008-08-29
backend@backend:~$ sudo blkid
[sudo] password for backend: 
/dev/sda2: UUID="cc87f4fc-3d1b-46bf-8ce7-22d5d4095fc4" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb2: UUID="f5eb4c7e-aca7-42b1-b7ed-8b2c16f1b7a8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: TYPE="swap" UUID="392731d5-7868-400d-82c0-f97793ed4f3f" 


backend@backend:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0cded2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         365     2931831   82  Linux swap / Solaris
/dev/sda2   *         366       32040   254429437+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfee0c03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2            1238       60801   478447830   83  Linux


backend@backend:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=cc87f4fc-3d1b-46bf-8ce7-22d5d4095fc4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=392731d5-7868-400d-82c0-f97793ed4f3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by bmwman on 2008-08-29
I added this to my fstab:
#dev/sdb2
UUID="f5eb4c7e-aca7-42b1-b7ed-8b2c16f1b7a8" /home/backend/Media deffaults 0   0

Is that gonna work and is that permanent?

---

### Post by iaculallad on 2008-08-29
I assume that the directory named /home/backend/Media exist in your filesystem. Add the line of text below on your fstab file:

```
gksudo gedit /etc/fstab
```

and insert the line of text on the last part of the file.

```
/dev/sdb1 /home/backend/Media           ext3    defaults  0 0
```

*Just perform a copy and paste.*

Save and Close.

---

### Post by iaculallad on 2008-08-29
> **bmwman said:**
> I added this to my fstab:
#dev/sdb2
UUID="f5eb4c7e-aca7-42b1-b7ed-8b2c16f1b7a8" /home/backend/Media deffaults 0   0

Is that gonna work and is that permanent?

That should be (If using the UUID):

```
UUID=f5eb4c7e-aca7-42b1-b7ed-8b2c16f1b7a8 /home/backend/Media ext3 defaults 0   0
```

---

### Post by bmwman on 2008-08-29
Well I've done that before, but if you saw my first post - /dev/sda and /dev/sdb sometimes switch after reboot. That's why I think I need to use the UUID but I don't really know the correct syntax.

BTW this didn't work at all:

> **bmwman said:**
> I added this to my fstab:
#dev/sdb2
UUID="f5eb4c7e-aca7-42b1-b7ed-8b2c16f1b7a8" /home/backend/Media deffaults 0   0

Is that gonna work and is that permanent?

---

### Post by bmwman on 2008-08-29
I got it to work :)
I spelled "defaults" incorrect and didn't have the ext3. It mounts now after I reboot and that should be permanent regardless of if the drive is sda or sdb, correct?

---

### Post by iaculallad on 2008-08-29
> **bmwman said:**
> I got it to work :)
I spelled "defaults" incorrect and didn't have the ext3. It mounts now after I reboot and that should be permanent regardless of if the drive is sda or sdb, correct?

It will always mount as sdb as you have pointed it to it's UUID.

---

### Post by bmwman on 2008-08-29
Sweeeeet. Thank you!

;)

---

