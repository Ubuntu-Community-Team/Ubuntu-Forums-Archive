---
title: "Install Ubuntu with alternate CD from harddisk"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by fusionBob on 2006-10-23
I copy the whole content of the alternate CD from 6.10RC to the first partition of the harddisk (where kanotix already lives).
I want to install ubuntu 6.10 RC from this copy without using CD-rom
or a network connection.

I found some documentation (ch05s01.html) on the CD and therefore 
I add the following to menu.lst of grub

title  New Install
kernel (hd0,0)/boot/ubuntu610rc/install/vmlinuz root=/dev/ram0 ramdisk_size=12000
initrd (hd0,0)/boot/ubuntu610rc/install/initrd.gz

The installation starts and search for the cdrom. That was not my intention.

I look in ch05s02.html and I try
title  New Install
kernel (hd0,0)/boot/ubuntu610rc/install/vmlinuz root=/dev/ram0 ramdisk_size=12000 *INSTALL_MEDIA_DEV=/dev/hda1/boot/ubuntu610rc*
initrd (hd0,0)/boot/ubuntu610rc/install/initrd.gz

The installer search again for a CDROM.
In a debian doc ([http://d-i.alioth.debian.org/manual/en.i386/apas02.html#howto-getting-images-hard-disk](http://d-i.alioth.debian.org/manual/en.i386/apas02.html#howto-getting-images-hard-disk)) I found that I should download hd-media/initrd.gz and hd-media/vmlinuz. Where are these files on the ubuntu 6.10 alternate install CD? I think the initrd.gz I use is only for cd-rom installation.
Any idea? Thank you very much.

---

### Post by john_spiral on 2006-10-23
try the initrd.gz & vmlinuz files from the below **hd-media** folder

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

caio

John

---

