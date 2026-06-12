---
title: "Fresh Karmic install dual-booted with Jaunty increased Jaunty's boot time"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by Shazaam on 2009-11-27
fdisk -lu...
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   419665994   209832966    5  Extended
/dev/sda5             126     4369679     2184777   82  Linux swap / Solaris
/dev/sda6         4369743   214194644   104912451   83  Linux
/dev/sda7       214194708   419665994   102735643+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000096f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312576704   156288321    7  HPFS/NTFS

```
sda6= Jaunty ext3 grub legacy.
sda7= Karmic ext4 grub2 on sda's mbr.
All os's boot and all partitions mount. From the start Jaunty's boot time increased to around 35 seconds. Ran bootchart on Jaunty to see where the bottleneck was; attached to post (right-click/save image as).

grub.cfg...
Karmic
```
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set 3b0453ab-a2ad-420f-88ad-7d79a722cc47
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=3b0453ab-a2ad-420f-88ad-7d79a722cc47 ro  splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
```
Jaunty
```
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sdb6)" {
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set 55357815-4cd9-4d5d-8696-234afcd7c0e3
	linux /boot/vmlinuz-2.6.28-16-generic root=/dev/sda6 ro quiet splash
	initrd /boot/initrd.img-2.6.28-16-generic
```
How could an install increase another distro's boot time? I know I shouldn't complain but it seems kind of odd.

---

