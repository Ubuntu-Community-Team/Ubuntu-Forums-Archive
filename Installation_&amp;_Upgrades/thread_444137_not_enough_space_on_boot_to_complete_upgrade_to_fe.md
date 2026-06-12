---
title: "not enough space on /boot to complete upgrade to feisty; what do I do?"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by icefaerie on 2007-05-15
Well, I attempted upgrading from edgy (2.6.17-11-386 #2 Tue Mar 13 23:30:30 UTC 2007 i686 GNU/Linux), to feisty, but my upgrade crashed with about 5 minutes remaining.

I did use the official upgrade method via the upgrade-manager.

The problem is that dpkg is trying to generate initrd.img-2.6.20-15-386, but unfortunately, my /boot does not have enough space for it.  When I first partitioned my HDD for ubuntu, I was migrating from Gentoo, where 32 MB was more than enough for /boot.  However, since I'm no longer rolling my own minimal kernels, the 64MB I partitioned has turned out not to be enough.

So, what can I do about this?  I am afraid to reboot lest I be left with some sort of dead system.  (Not having udev is probably not good.)

These are the sorts of errors I am getting.

```
Setting up udev (108-0ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-2.6.20-15-386
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
dpkg: error processing udev (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured

```

And so on.  Here is relevant disk space info.

```
liz@yaoi:/boot$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              19G   12G  7.0G  63% /
varrun                248M  116K  248M   1% /var/run
varlock               248M  4.0K  248M   1% /var/lock
procbususb             10M  132K  9.9M   2% /proc/bus/usb
udev                   10M  132K  9.9M   2% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   18M  230M   8% /lib/modules/2.6.17-11-386/volatile
/dev/hda2              59M   46M   11M  82% /boot
/dev/hdb4             139G  135G  4.2G  98% /mnt/gentoo
/dev/hdd1             233G  228G  5.5G  98% /mnt/new
/dev/hdb1              31M   18M   11M  63% /mnt/oldboot
/dev/hdb3             9.6G  7.4G  2.2G  78% /mnt/share
/dev/hda1              19G   13G  6.3G  67% /mnt/windows
tmpfs                 248M   33M  215M  14% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 248M   34M  214M  14% /lib/modules/2.6.20-15-386/volatile
liz@yaoi:/boot$ ls -lh
total 42M
-rw-r--r-- 1 root root 280K 2007-03-13 19:46 abi-2.6.17-11-386
-rw-r--r-- 1 root root 402K 2007-04-15 04:01 abi-2.6.20-15-386
-rw-r--r-- 1 root root 405K 2007-04-15 04:07 abi-2.6.20-15-generic
-rw-r--r-- 1 root root  74K 2007-03-13 17:42 config-2.6.17-11-386
-rw-r--r-- 1 root root  82K 2007-04-15 01:04 config-2.6.20-15-386
-rw-r--r-- 1 root root  82K 2007-04-15 01:33 config-2.6.20-15-generic
drwxr-xr-x 2 root root 1.0K 2007-05-15 02:51 grub
-rw-r--r-- 1 root root 6.7M 2007-04-12 11:26 initrd.img-2.6.17-11-386
-rw-r--r-- 1 root root 6.8M 2007-05-15 00:30 initrd.img-2.6.17-11-generic.bak
-rw-r--r-- 1 root root    0 2007-05-15 03:29 initrd.img-2.6.20-15-386
-rw-r--r-- 1 root root 7.9M 2007-05-15 02:51 initrd.img-2.6.20-15-386.bak
-rw-r--r-- 1 root root 3.8M 2007-05-15 03:29 initrd.img-2.6.20-15-386.dpkg-bak
-rw-r--r-- 1 root root 7.9M 2007-05-15 02:48 initrd.img-2.6.20-15-generic
drwxr-xr-x 2 root root  12K 2006-06-20 15:09 lost+found
-rw-r--r-- 1 root root  93K 2006-10-20 07:44 memtest86+.bin
-rw-r--r-- 1 root root 699K 2007-03-13 19:46 System.map-2.6.17-11-386
-rw-r--r-- 1 root root 771K 2007-04-15 04:03 System.map-2.6.20-15-386
-rw-r--r-- 1 root root 789K 2007-04-15 04:08 System.map-2.6.20-15-generic
-rw-r--r-- 1 root root 1.6M 2007-03-13 19:46 vmlinuz-2.6.17-11-386
-rw-r--r-- 1 root root 1.6M 2007-04-15 04:01 vmlinuz-2.6.20-15-386
-rw-r--r-- 1 root root 1.7M 2007-04-15 04:07 vmlinuz-2.6.20-15-generic

```

---

### Post by icefaerie on 2007-05-15
Of course, just after I post that, I notice there are a few files on /boot I can move elsewhere temporarily.... Did that and the upgrade finished.  Will be rebooting and hoping it works.

---

