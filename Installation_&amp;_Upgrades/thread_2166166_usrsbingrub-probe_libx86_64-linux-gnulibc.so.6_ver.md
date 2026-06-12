---
title: "/usr/sbin/grub-probe: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.17' not found"
date: 2013-08-08
forum: Installation &amp; Upgrades
---

### Post by buggiz on 2013-08-08
I'm running ubuntu 12.04 and got into abit of trouble..
Anybody got an idea on what to do?

root@easy:/usr/local# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.5.0-23-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 156 MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 157743 files and directories currently installed.)
Removing linux-image-3.5.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
/usr/sbin/grub-probe: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.17' not found (required by /lib/x86_64-linux-gnu/libudev.so.0)
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.5.0-23-generic.postrm line 328.
dpkg: error processing linux-image-3.5.0-23-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.5.0-23-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

