---
title: "Boot fails: ALERT! /dev/sda1 does not exist"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by plg on 2006-09-19
After a recent update, newer kernels fail to boot.

ALERT! /dev/sda1 does not extist... Dropping to shell...

I have an AMD Athlon64 X2 (dual core) and two SATA disks.
The bootable is (hd0,0) -> /dev/sda1  is the root partition.

Installation is based on Breezy 5.10.
The following kernels are installed:

* linux-image-2.6.12-10-amd64-k8
* linux-image-2.6.12-9-amd64-k8
* linux-image-2.6.12-9-amd64-generic

The only kernel that boots is "amd64-generic", the other two have been reinstalled after problems began. But with no luck.

I have tried a bunch of things:

$ sudo dpkg-reconfigure udev
$ sudo dpkg-reconfigure initramfs-tools

(installed initrd-tools - which wasn't there)

$ sudo mkinitrd -o initrd.img-2.6.12-10-amd-k8 2.6.12-10-amd64-k8
(spat out a bunch of warnings of missing options and did not produce an initrd image)

$ sudo mkinitramfs -o initramfs.img-2.6.12-10-amd-k8 2.6.12-10-amd64-k8

produced a nice image - but did not solve the problem (edited GRUB to use the correct image).

Kind of pretty lost here.  I've seen other threads discuss this boot problems and the above stuff have helped. Not in my case though. ](*,)


BTW, Installing ATI drivers for lib64 seems to do strange things. It installs 32-bit libraries in /lib (/usr/X11R6/lib) which overwrites the ones installed in /lib64...  I copied and renamed lib64 to point to lib64-real.  But it feels kind of unsafe. Any other hints?

/ Patric

---

