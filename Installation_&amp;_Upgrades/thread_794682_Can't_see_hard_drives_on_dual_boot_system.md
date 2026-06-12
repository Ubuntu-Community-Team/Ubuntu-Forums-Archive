---
title: "Can't see hard drives on dual boot system"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by killerbread on 2008-05-14
So I recently installed Ubuntu 8.04 with windows XP. Ubuntu is on a second partition an the same hard drive as windows. The problem is that I lost a 400 gb SATA drive in Ubuntu. Windows recognizes it just fine though.

entering: cat /etc/mtab

produces:

/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/andrew/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=andrew 0 0
/dev/sdb1 /media/Backup fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
-----------------------------------------------------------------

and entering: sudo fdisk -l

produces:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x256bc023

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5436    43664638+   7  HPFS/NTFS
/dev/sda2            5437       14593    73553602+   5  Extended
/dev/sda5            5437       14215    70517286   83  Linux
/dev/sda6           14216       14593     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7988960

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

-------------------------------------------------------------------

Ubuntu recognizes a external hard drive just fine, adding to my confusion.
:(:confused:

---

### Post by jwmislan on 2008-06-02
Take a look at this thread - it should be of some help to you.
[http://ubuntuforums.org/showthread.php?t=809926](http://ubuntuforums.org/showthread.php?t=809926)

JWM

---

