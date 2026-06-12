---
title: "[SOLVED] Problems with upgrade to linux-image-2.6.24-21-generic"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by knuno on 2008-10-24
After running an ordinary update through Adept I got a problem upgrading linux-image-2.6.24-21-generic. I have tried to run sudo dpkg --configure -a, which gives the following output:
```
Setting up linux-image-2.6.24-21-generic (2.6.24-21.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
mv: cannot move `/tmp/fileGu5MZc' to `/TMP/FILEGU5MZC': No such file or directory
mv: cannot move `/var/run/grub/menu.lst' to `/VAR/RUN/GRUB/MENU.LST': No such file or directory
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.24-21-generic

```
I have tried to run apt-get clean and apt-get install -f to no avail.

The mv commands seem a little odd to me?

Any ideas anyone?

Knut

---

### Post by knuno on 2008-11-06
Having upgraded to 8.10 this problem is not relevant for me anymore.

Knut

---

