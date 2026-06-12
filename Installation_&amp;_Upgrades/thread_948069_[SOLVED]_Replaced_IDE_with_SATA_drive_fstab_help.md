---
title: "[SOLVED] Replaced IDE with SATA drive fstab help"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by Skeorx13 on 2008-10-14
I recently installed a new 1.5 TB sata drive to my system. Ubuntu (parted) didn't want to format the drive so I had to do it in windoze. So the drive is in NTFS format. Once I loaded up ubuntu I almost expected it to auto mount. It did not. I could however just click on it in the places menu and it mounted fine. However, after removing the IDE drive that it would be replacing (the only IDE drive I had left) the fstab did not update. In the fstab file the lines for the old IDE drive are still there. I tried editing the fstab to add the new drive which mounts at sdc1 with its proper UUID (found in the volume tab of the properties menu) and using the same parameters as the other two NTFS drives that are connected (one which WAS connected but no longer is). Upon rebooting the drive does NOT autoload and upon trying to mount the drive it now says I do not have the privileges (or something along those lines) to mount it. This seems strange to me since my other NTFS drive that automounts and has the proper mounting point and UUID and the exact same options loads by itself perfectly fine. Can anyone help me figure out why I am not allowed to do this???

My current fstab after editing:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sd[COLOR="Red"]**c**[/COLOR]1
UUID=d87a4a93-95d0-4165-a876-dd1093687c4f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=DAF40A6AF40A4969 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=00983E7D983E7170 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=0660A2CF60A2C531 /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
The red seemed to be an error in placement after the IDE drive was removed, but since it is commented out I assume this is moot. The UUID=DAF40A6AF40A4969 line is the removed IDE drive. 
Currently sda1 is my ubuntu sata drive (UUID=d87a4a93-95d0-4165-a876-dd1093687c4f), sdb1 is my main windows xp drive (UUID=00983E7D983E7170), and sdc1 is where the new drive is mounted (UUID=0660A2CF60A2C531). scd0 is the sata DVD+RW drive.

---

### Post by caljohnsmith on 2008-10-15
Open up a terminal (applications > accessories > terminal), and please post the following:
```
sudo fdisk -lu
sudo blkid
```
That will hopefully clarify what your current HDD setup is.

---

### Post by Skeorx13 on 2008-10-15
fdisk
> 
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x758c758c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   586099394   293049666   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe94ae94a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625121279   312560608+   7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bf591

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  2930272064  1465136001    7  HPFS/NTFS

> 
/dev/sda1: UUID="d87a4a93-95d0-4165-a876-dd1093687c4f" TYPE="ext3" 
/dev/sdb1: UUID="00983E7D983E7170" LABEL="Windows primary" TYPE="ntfs" 
/dev/sdc1: UUID="0660A2CF60A2C531" LABEL="Media" TYPE="ntfs" 


---

### Post by caljohnsmith on 2008-10-15
It looks to me like your fstab entry for sdc1 should work. This is a really small thing, but have you checked to make sure you have a /media/sdc1 directory created? If so, I'm not sure what the problem is.

---

### Post by Skeorx13 on 2008-10-18
Hmm, that'd be a rather stupid thing to need to do... But no it wasn't there. I'll make the dir and see how that goes.

Edit:
/facepalm
Yup that was it. You'd think the fstab would automatically create the mount directory. Apparently not. Thanks for the help.

---

