---
title: "[SOLVED] wrong /boot updated from Gutsy to Hardy"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by jsimerly on 2008-05-08
I've been using Ubuntu since 6.06 and have upgraded through all subsequent versions smoothly until Hardy came along.  Basically, I have a Hardy installation which cannot boot to the 2.6.24 kernel and is stuck on the earlier 2.6.22 and -20 releases.

root@harmony12:~# fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000024f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          18      144553+  83  Linux
/dev/sda2              19        9039    72461182+   5  Extended
/dev/sda5              19        9039    72461151   8e  Linux LVM

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00020a8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    5  Extended
/dev/sdb5               1       36483   293049634+  8e  Linux LVM

I am using two SATA disks.  sda contains rootvg, which houses the LVs sda1, sda2, and sda3 shown above.  /dev/sda1 is the boot LV.  /dev/sda5 is a Linux LVM partition which houses the / and /usr file systems.  sdb contains all of the other file systems, ie, /home, /var, /etc in the Linux LVM sdb5.

root@harmony12:~# lvm
lvm> lvscan
  ACTIVE            '/dev/rootvg/root_lv' [5.00 GB] inherit
  ACTIVE            '/dev/rootvg/usr_lv' [15.00 GB] inherit
  ACTIVE            '/dev/rootvg/swap_lv' [5.00 GB] inherit
  ACTIVE            '/dev/home_data_vg/home_lv' [20.00 GB] inherit
  ACTIVE            '/dev/home_data_vg/var_lv' [5.00 GB] inherit
  ACTIVE            '/dev/home_data_vg/var_log_lv' [5.00 GB] inherit
  ACTIVE            '/dev/home_data_vg/usr_local_lv' [10.00 GB] inherit
  ACTIVE            '/dev/home_data_vg/srv_lv' [5.00 GB] inherit
  ACTIVE            '/dev/home_data_vg/src_lv' [10.00 GB] inherit
  ACTIVE            '/dev/home_data_vg/tmp_lv' [5.00 GB] inherit
  ACTIVE            '/dev/home_data_vg/opt_lv' [5.00 GB] inherit
  ACTIVE            '/dev/home_data_vg/backup' [50.00 GB] inherit

The LVM-managed root_lv contains a directory called /boot.  It is this directory that got updated with all of the latest 2.6.24 images and menu.lst entries.  The /boot directory that lives on /dev/sda1 did not get updated and leaves my system stuck with the old Ubuntu 7.10 entries and 2.6.22 and earlier kernels.  I even changed the bootable flag from /dev/sda1 to /dev/sda5 using the Live CD gparted.  The system still boots using the outdated contents of /dev/sda1.

Here is the fstab file:

root@harmony12:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/rootvg-root_lv /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1 -- converted during upgrade to edgy
UUID=89fde834-d7dd-4b97-9ebb-88f4f503ab11 /boot ext3 defaults 0 2
/dev/mapper/home_data_vg-home_lv /home           ext3    defaults        0       2
/dev/mapper/home_data_vg-opt_lv /opt            ext3    defaults        0       2
/dev/mapper/home_data_vg-src_lv /source         ext3    defaults        0       2
/dev/mapper/home_data_vg-srv_lv /srv            ext3    defaults        0       2
/dev/mapper/home_data_vg-tmp_lv /tmp            ext3    defaults        0       2
/dev/mapper/rootvg-usr_lv /usr            ext3    defaults        0       2
/dev/mapper/home_data_vg-usr_local_lv /usr/local      ext3    defaults        0       2
/dev/mapper/home_data_vg-var_lv /var            ext3    defaults        0       2
/dev/mapper/home_data_vg-var_log_lv /var/log        ext3    defaults        0       2
/dev/mapper/home_data_vg-backup /backup        ext3    defaults         0       2
/dev/mapper/rootvg-swap_lv none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

When I boot using the 8.04 Live CD, I can mount /dev/sda1 to a mount point and see the old 7.10 entries and kernels.  However, I cannot mount the /boot directory because it resides in the LVM-controlled root directory /dev/rootvg/root_lv.  That leaves me unable to copy the contents of /boot to the old /boot on /dev/sda1.

This would seem not to be a great solution anyway, as it leaves me asking why previous upgrades successfully wrote to the /boot directory on /dev/sda1 and why the Hardy upgrade wrote only to the /boot directory on the LVM-controlled / filesystem.

Is there a way to direct the boot process successfully to the LVM-controlled /boot directory rather than the old and outdated directory contained on /dev/sda1 so that future upgrades bring their kernel and updated boot entries with them?

---

### Post by bobnutfield on 2008-05-08
You may have already checked this, but a lot of people who upgraded elected to keep their original menu.lst file instead of letting Hardy update it.  If this is the case, you might check and make sure there is an entry for it and that it is the default boot kernel.  As I am sure you know, the first entry will boot first.

Bob

---

### Post by jsimerly on 2008-05-08
Bob, thanks for the reply.  I don't think that's the problem.  You can see that the first entry calls for the Ubuntu 8.04 2.6.24-17 kernel.

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.24-17-generic root=/dev/mapper/rootvg-root_lv ro quiet splash
initrd          /initrd.img-2.6.24-17-generic

title           Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.24-17-generic root=/dev/mapper/rootvg-root_lv ro single
initrd          /initrd.img-2.6.24-17-generic

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.24-16-generic root=/dev/mapper/rootvg-root_lv ro quiet splash
initrd          /initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.24-16-generic root=/dev/mapper/rootvg-root_lv ro single
initrd          /initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/rootvg-root_lv ro quiet splash
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/rootvg-root_lv ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 8.04, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/rootvg-root_lv ro quiet splash
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/rootvg-root_lv ro single
initrd          /initrd.img-2.6.20-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

Here's what booted:

Here's what really running:

root@harmony12:~# uname -r
2.6.22-14-generic

The only entries available at boot time are:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, kernel 2.6.20-16-generic
Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
memtest

I have verified that those entries are available only in the menu.lst contained on /dev/sda1, not the menu.lst file on the currently-mounted /boot directory in /.

---

### Post by bobnutfield on 2008-05-08
That is odd, but what I would do is simply replace the menu.lst in the /boot directory with the one shown on /sda1, adding any additional entries, assuming they will point to this as well:

> root=/dev/mapper/rootvg-root_lv ro singl

I don't use LVM's just for this reason.  Sometimes upgrades confuse things and repairing it is tricky with LVM's.

Bob

---

### Post by jsimerly on 2008-05-10
Replacing the menu.lst would not solve the problem, either.  No matter what I've done so far, the system boots from /dev/sda1 and uses its outdated menu entries and old kernels.

---

### Post by jsimerly on 2008-05-18
Reinstalled 8.04 from Alternate CD.  Kept existing partitions intact and let install format only non-user data partitions, /, /usr, /boot, and /var.

---

