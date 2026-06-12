---
title: "Unable to write to mounted drive"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by driscollw on 2008-05-10
Hello, 
  I have read through the forums and have gotten my secondary sata drive to mount but, I am unable to write to it ?  trying to mount sdb1 to /media/SATA2. The drive mounts and shows a 80.0GB drive on my desktop, just can´t use it ? Thank you for any help you can provide. 

Here is my fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99cc99cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        9729    77899185    5  Extended
/dev/sda5              32        9729    77899153+  8e  Linux LVM

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0373fc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
driscollw@william:~$ 


Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/william-root
UUID=5b43d79e-40d5-4b2c-ab0b-12b8d3524a01 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7a9faf78-82a9-4d80-b257-de4ddfc230f0 /boot           ext3    relatime        0       2
# /dev/mapper/william-swap_1
UUID=d1497dc8-d52a-4839-9001-fbbc250d029d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=782979db-d9a7-4602-880c-0c9dca83fa5c /media/SATA2  ext3 auto,user      0       2

Here is my blkid

 sudo blkid
/dev/mapper/william-root: UUID="5b43d79e-40d5-4b2c-ab0b-12b8d3524a01" TYPE="ext3" 
/dev/mapper/william-swap_1: TYPE="swap" UUID="d1497dc8-d52a-4839-9001-fbbc250d029d" 
/dev/sda1: UUID="7a9faf78-82a9-4d80-b257-de4ddfc230f0" TYPE="ext3" 
/dev/sda5: UUID="SvacRY-BOar-2fPn-xQZ4-kq4A-yeY6-IMGHDX" TYPE="lvm2pv" 
/dev/sdb1: UUID="782979db-d9a7-4602-880c-0c9dca83fa5c" TYPE="ext3"

---

### Post by Pumalite on 2008-05-10
Maybe a matter of permissions:
sudo chmod 777 /media/SATA2

---

### Post by driscollw on 2008-05-10
That fixed it. What do I need to put in my fstab to do this on bootup ? 
Thank you,

---

### Post by Pumalite on 2008-05-10
This is an example. Change to your needs correspondingly:

# /dev/sdc2
UUID=d7613213-0687-4000-a4ba-6fef1a95d082 /media/sdc2     ext3    defaults        0       2

Get the UUID with 'blkid' in Terminal

---

### Post by driscollw on 2008-05-10
Thank you very much, I edited my fstab and after a reboot everything is working fine.

---

### Post by Pumalite on 2008-05-10
You are welcome. Good luck.

---

