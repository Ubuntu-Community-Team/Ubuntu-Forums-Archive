---
title: "how to stop apt-get from rebuilding initrd?"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2010-03-02
after every call to apt-get, I encounter the following issue:

```
Setting up linux-image-2.6.32.9-custom (2.6.32.9-custom-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.32.9-custom
) points to /boot/initrd.img-2.6.32.9-custom
 (/boot/initrd.img-2.6.32.9-custom) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.32.9-custom.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.32.9-custom
) points to /boot/vmlinuz-2.6.32.9-custom
 (/boot/vmlinuz-2.6.32.9-custom) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.32.9-custom.postinst line 588.
Running postinst hook script update-grub.
User postinst hook script [update-grub] failed to execute: No such file or directory
dpkg: error processing linux-image-2.6.32.9-custom (--configure):
 subprocess installed post-installation script returned error exit status 255
Setting up thunderbird-gnome-support (2.0.0.23+build1+nobinonly-0ubuntu1) ...
Errors were encountered while processing:
 linux-image-2.6.32.9-custom
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


how do I stop apt-get from doing this? appearantly, the system runs fine without this initrd thing. also, this takes quite a long time, and gives an error after each apt-get

(the kernel in question was build according to the instructions on how to build an upstream kernel.)

---

