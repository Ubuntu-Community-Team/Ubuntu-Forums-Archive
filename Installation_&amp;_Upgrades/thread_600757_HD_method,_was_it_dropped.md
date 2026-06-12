---
title: "HD method, was it dropped?"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by IronWolve on 2007-11-02
I have the gutsy install dvd, and the /installcd directory was missing.

I wanted to do the normal, copy the dvd, add install to grub, and do it that way.

Anyone noticed this?

---

### Post by IronWolve on 2007-11-02
Basically the install from HD is the following.

(This is from CD, but DVD should be the same)

$ mkdir /tmp/installcd
$ sudo mount -o loop /path/to/ubuntu-7.04-desktop-i386.iso /tmp/installcd
$ sudo mkdir /mnt/installer
$ sudo mount /dev/hda3 /mnt/installer
$ sudo cp -r /tmp/installcd/* /mnt/installer
$ sudo umount /tmp/installcd


Edit grub.

title disk-installer
root (hd0,2)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd /casper/initrd.gz

---

