---
title: "can't boot after apt-get dist-upgrade, grub error 13"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by bcrowell on 2006-08-06
Last night I did an apt-get dist-upgrade to upgrade from breezy to dapper. Everything seemed to have gone fine, although now that I look back, I realize that I probably didn't actually reboot after the upgrade.

This morning my machine wouldn't boot, and I'm having to post this after booting with a knoppix cd. I have backups, but I'd like to avoid a fresh install, if possible.

Here is the error message from GRUB:

Booting 'Ubuntu, kernel 2.6-xen0 '
... (hd0,0)
Filesystem type is ext2fs, partition type 0x83
Kernel /boot/vmlinuz-2.6-xen0 root=/dev/hda1 ro quiet splash
Error 13: Invalid or unsupported executable format

A more detailed description of error 13 is: "The kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD)."

Looking around on the forums, I do find other people who have had error 13, but they all seem to be people who are dual booting, or who have done something complicated with their partitioning. I'm not dual-booting, and my partitioning is just the default that ubuntu originally gave me.

Waaaaa! Can anybody suggest anything? :cry:

---

