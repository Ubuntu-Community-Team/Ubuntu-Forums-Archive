---
title: "Reiserfs read-only why ?"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Larion on 2009-04-10
Hi,

I have installed 9,04 beta 1 week ago. Since then I have been dealing with the same error while booting.

File system seems mounted read-only
and it is checking somethink about journals 
then starts ubuntu.

My fstab looks like this

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c7efbde1-4284-4cac-b360-fb407eb1aed8 /               reiserfs notail,relatime 0       1
# swap was on /dev/sda5 during installation
UUID=37e50d0f-becc-4caa-b17c-bc1ca6a11c5d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sdd1	/media/Seagate	ntfs-3g	defaults	0	0
/dev/sdb1	/media/Samsung	ntfs-3g defaults	0	0
/dev/sdc1	/media/Seagate-1	ntfs-3g	defaults	0	0
```

How can I fix this ?
Regards

---

### Post by Larion on 2009-04-11
bump

---

### Post by Larion on 2009-04-12
noone knows why ?

---

### Post by deanjm1963 on 2009-04-12
The root file systems are mounted as read only during boot. ReiserFS checks the journal of each partition with ReiserFS on each and every boot.

JFS and XFS also check the journals on each boot, but their checking is very quick compared to ReiserFS.

Hope this helps.

---

### Post by Larion on 2009-04-13
I know that it is mounted read only. 

How can I change this ?
Do I have to wait for fsck to check the drive everytime I reboot ?

I didn't have such problem using Ext4 and Ext3. 

Or is it in ReiserFS's nature to mount root read-only and check each restart ?

I am trying to find out if this is a problem, bug or a feature.

Regards

---

