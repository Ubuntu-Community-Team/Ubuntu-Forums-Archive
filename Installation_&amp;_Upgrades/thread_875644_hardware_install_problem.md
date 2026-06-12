---
title: "hardware install problem"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by jeffpdx on 2008-07-31
I read _Add another Hard Drive to Ubuntu_ at xawk.com following it and making changes where my device had different names.

I can't find my new mounted drive.

sudo mount /dev/sdb1 /nas2

returns:

according to mtab, /dev/sdb1 is already mounted on /nas2

however Places, Computer does not show it nor is it mounted on the desktop.

---

### Post by iaculallad on 2008-07-31
> **jeffpdx said:**
> I read _Add another Hard Drive to Ubuntu_ at xawk.com following it and making changes where my device had different names.

I can't find my new mounted drive.

sudo mount /dev/sdb1 /nas2

returns:

according to mtab, /dev/sdb1 is already mounted on /nas2

however Places, Computer does not show it nor is it mounted on the desktop.

Post whatever displays when you issue the following commands on your terminal:

```
cat /etc/fstab
sudo fdisk -l
sudo blkid
```

---

### Post by jeffpdx on 2008-07-31
Okay so one reboot didn't do the trick but two did. Today it is mounted on boot. I'll re post if there is a further problem but it seems to be fixed. I ran the commands however and here is the output; perhaps someone else may benifit.
Okay here goes:

oem@freekbox:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
# /dev/sdb1	/nas2		ext3	defaults	0	0
UUID=d2bb1821-0d87-47a0-b072-4d0f4a782bd4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4214c7a2-d166-449a-b994-6d33f9a9cea3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
oem@freekbox:~$ sudo fdisk -l
[sudo] password for oem: 

Disk /dev/sda: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd15e3baa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3597    28892871   83  Linux
/dev/sda2            3598        3737     1124550    5  Extended
/dev/sda5            3598        3737     1124518+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd9c74ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9964    80035798+  83  Linux
oem@freekbox:~$ sudo blkid
/dev/sda1: UUID="d2bb1821-0d87-47a0-b072-4d0f4a782bd4" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="4214c7a2-d166-449a-b994-6d33f9a9cea3" 
/dev/sdb1: UUID="9ed4aaa4-efa8-4d80-81cc-a1a2e7a2aed6" TYPE="ext3" 
oem@freekbox:~$

---

### Post by falcon61102 on 2008-07-31
Sometimes when you mount a drive the way you did, it will mount but an icon won't appear on the desktop or in the Places menu.  I think this may have something to do with not mounting it in the /media folder.  So instead of mounting it as:
```
sudo mount /dev/sdb1 /nas2
```
Try using:
```
sudo mount /dev/sdb1 /media/nas2
```

---

### Post by jeffpdx on 2008-08-01
Great! Thanks!

When I add users or change my username will I have to go in and give permissions manually to each added drive or does users and groups take care of that. ie is there a gui equivelent when updating?

---

### Post by falcon61102 on 2008-08-01
Users and Groups should automatically take care of that.  If you're asking if there is a GUI way to update user names and what not, then yes there is.  You can either right-click on your user name in the upper right hand corner of your desktop or go through System>Administration>Users and Groups.

---

