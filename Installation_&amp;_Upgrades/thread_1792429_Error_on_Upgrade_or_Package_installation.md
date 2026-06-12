---
title: "Error on Upgrade or Package installation"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by mobius129a on 2011-06-28
Kernel version: 2.6.32-30-generic
Distro: Ubuntu 10.04

Whenever I install a new package or upgrade, I get the following error:

```
Setting up linux-image-2.6.32-31-generic (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 14: quiet: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-2.6.32-32-generic (2.6.32-32.62) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-32-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 14: quiet: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-32-generic; however:
  Package linux-image-2.6.32-32-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.32.38); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            No apport report written because MaxReports has already been reached
                                                                                                                                                                                Errors were encountered while processing:
 linux-image-2.6.32-31-generic
 linux-image-2.6.32-32-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```The error does not however prevent packages from being installed nor does it prevent packages from being upgraded. However, I'd like to find the root of the problem and how I can resolve it.

TIA.

---

### Post by mobius129a on 2011-06-28
Also, all of the problem packages (linux-generic packages) on the post above are already installed.

---

