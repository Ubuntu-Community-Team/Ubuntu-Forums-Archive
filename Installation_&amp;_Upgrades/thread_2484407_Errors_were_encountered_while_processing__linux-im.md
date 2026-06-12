---
title: "Errors were encountered while processing:  linux-image-5.15.0-67-generic  linux-image"
date: 2023-02-25
forum: Installation &amp; Upgrades
---

### Post by foord on 2023-02-25
Hi 
I've just upgraded to the latest version of Ubuntu ( 22.04.2 LTS). Following that an appImage programme stopped working. So I tried to download a FUSE2 package that it requires. 
 
However, I got the following error when installing. I think I've seen something like this elsewhere when rebooting or starting (it might flash up briefly - but I can't be sure).

Found linux image: /boot/vmlinuz-5.19.0-32-generic
Found initrd image: /boot/initrd.img-5.19.0-32-generic
Found linux image: /boot/vmlinuz-5.15.0-67-generic
Found initrd image: /boot/initrd.img-5.15.0-67-generic
Found linux image: /boot/vmlinuz-5.15.0-66-generic
Found initrd image: /boot/initrd.img-5.15.0-66-generic
Found linux image: /boot/vmlinuz-5.15.0-58-generic
Found initrd image: /boot/initrd.img-5.15.0-58-generic
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.s
o.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.19.0-32-generic (--configure):
 installed linux-image-5.19.0-32-generic package post-installation script subpro
cess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.15.0-67-generic
 linux-image-5.19.0-32-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas?

---

### Post by MAFoElffen on 2023-02-25
Part of this Bug: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1969353](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1969353)

Problem is fixed in comment #23:
> 
download and install libssl1.1 from the Impish archive ([https://packages.ubuntu.com/impish/libssl1.1](https://packages.ubuntu.com/impish/libssl1.1))


---

