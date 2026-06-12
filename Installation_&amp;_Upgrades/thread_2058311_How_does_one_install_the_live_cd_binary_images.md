---
title: "How does one install the live cd binary images"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by robertgordonkey on 2012-09-15
Hi I have at long last successfully build a live ubuntu 12.04 image using Live-build and Colin Watson's config files from livecd-rootfs.   I have these files in the build directory.

binary.headers
 livecd.ubuntu.initrd-generic
binary.list
 livecd.ubuntu.kernel
binary.log
 livecd.ubuntu.kernel-generic
binary.packages.install
 livecd.ubuntu.manifest
binary.packages.live
 livecd.ubuntu.manifest-remove
cache                    livecd.ubuntu.size
chroot                   livecd.ubuntu.squashfs

Does anyone know how to create the iso image from these files? I presume once I have the iso image I can install it to a usb drive with:

dd if=liveubuntu.iso of=/dev/sdc bs=4M

Thanks, any help would be appreciated.
 Robert

---

### Post by Bucky Ball on 2012-09-15
*Thread moved to **Installation & Upgrades***

---

