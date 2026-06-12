---
title: "Cannot boot into LiveCD"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by bredelet on 2007-03-31
I want to install Ubuntu on my Thinkpad 240.

When I try to boot into the live CD, I get thrown into "initramfs".

It looks like it cannot mount the squashfs image:

(initramfs) ls -F mnt
livecd/
(initramfs) mount -t squashfs /cdrom/casper/filesystem.squashfs mnt/livecd
mount: Couldn't setup loop device
mount: Mounting (null) on mnt/livecd failed: No such file or directory
(initramfs) modprobe loop
(initramfs) losetup -f
losetup: could not find any device /dev/loop#

I have 196MB RAM

---

### Post by bredelet on 2007-04-23
OK I worked aruond the problem by installing Ubuntu on a different computer and copying the disk on this one.

Now I need to reconfigure everything....

---

