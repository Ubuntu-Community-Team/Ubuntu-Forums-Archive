---
title: "Cannot boot after new installation"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by Adam_Healy on 2015-03-18
I installed 14.04 on a new SSD. Upoon restart after the installation, I got a boot error that the boot loader was trying to boot of the PCIe Controller (this is last in the boot order).

I thought it may be an issue with grub not installed propery. I boot into ubuntu from my flash drive and ran boot repair. After restarting i get the following error message:
Booting in insecure mode
Failed to open \EFI\BOOT\grubx64.efi - 800000000000000E
Failed to load image
Failed to open \EFI\BOOT\MokManager.efi - 800000000000000E
Failed to load image
_

This error message remains until I restart. I assume there is something I need to configure, but I can't figure out what that is. Here is a link to the file from boot repair [http://paste.ubuntu.com/10622450/](http://paste.ubuntu.com/10622450/)

---

