---
title: "Kernel Install Error"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by DocHoliday52090 on 2007-05-15
I need to compile a new kernel for Suspend2. I've done it before for other patches many times, all successful. 

This time around, however, I received an error when installing the .debs:

```
root@Laptop:/usr/src# dpkg -i linux-image-2.6.21-custom_2.6.21-custom-10.00.Custom_i386.deb
(Reading database ... 147522 files and directories currently installed.)
Preparing to replace linux-image-2.6.21-custom 2.6.21-custom-10.00.Custom (using linux-image-2.6.21-custom_2.6.21-custom-10.00.Custom_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.21-custom ...
Running postrm hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.21-custom
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.21-custom (2.6.21-custom-10.00.Custom) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.21-custom
find: /lib/firmware/2.6.21-custom: No such file or directory
find: /lib/firmware/2.6.21-custom: No such file or directory
find: /lib/firmware/2.6.21-custom: No such file or directory
find: /lib/firmware/2.6.21-custom: No such file or directory
find: /lib/firmware/2.6.21-custom: No such file or directory
find: /lib/firmware/2.6.21-custom: No such file or directory
Failed to symbolic-link boot/initrd.img-2.6.21-custom to initrd.img.
dpkg: error processing linux-image-2.6.21-custom (--install):
 subprocess post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-2.6.21-custom

```

It seems as if it's having problems with initrd. 

Any suggestions?

---

### Post by DocHoliday52090 on 2007-05-15
Never mind, I fixed it. 

I removed the broken vmlinux and initrd links as well as the existing vmlinux.old and initird.old files  in the / directory. 

Install works fine now.

---

