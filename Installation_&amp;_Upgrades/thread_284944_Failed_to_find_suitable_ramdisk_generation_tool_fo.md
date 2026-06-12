---
title: "Failed to find suitable ramdisk generation tool for kernel version"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by dp_wiz on 2006-10-26
Can't install package "linux-image-2.6.17-10-386".
```

Setting up linux-image-2.6.17-10-386 (2.6.17-10.33) ...
Running depmod.
Finding valid ramdisk creators.
Failed to find suitable ramdisk generation tool for kernel version 
2.6.17-10-386 on running kernel 2.6.15-26-686 in /usr/sbin/mkinitramfs
dpkg: error processing linux-image-2.6.17-10-386 (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of linux-image-386:
 linux-image-386 depends on linux-image-2.6.17-10-386; however:
  Package linux-image-2.6.17-10-386 is not configured yet.
dpkg: error processing linux-image-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.17-10-386:
 linux-restricted-modules-2.6.17-10-386 depends on linux-image-2.6.17-10-386; however:
  Package linux-image-2.6.17-10-386 is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.17-10-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-386:
 linux-restricted-modules-386 depends on linux-restricted-modules-2.6.17-10-386; however:
  Package linux-restricted-modules-2.6.17-10-386 is not configured yet.
dpkg: error processing linux-restricted-modules-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-386:
 linux-386 depends on linux-image-386; however:
  Package linux-image-386 is not configured yet.
 linux-386 depends on linux-restricted-modules-386; however:
  Package linux-restricted-modules-386 is not configured yet.
dpkg: error processing linux-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-glx:
 nvidia-glx depends on nvidia-kernel-1.0.8774; however:
  Package nvidia-kernel-1.0.8774 is not installed.
  Package linux-restricted-modules-2.6.17-10-386 which provides nvidia-kernel-1.0.8774 is not configured yet.
dpkg: error processing nvidia-glx (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.17-10-386
 linux-image-386
 linux-restricted-modules-2.6.17-10-386
 linux-restricted-modules-386
 linux-386
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried to install yaird and reinstall mkinitramfs but that is unhelpful.

Next boot i've got not-working "nvidia" driver for xorg because of version mismatch with kernel module.

---

### Post by itsmabus on 2007-02-11
I have the same problem with booting, only it's with the server kernel instead.

---

### Post by whistl on 2007-02-12
I had the exact same problem, and fixed it by editing /etc/kernel-img.conf and removing the line:

ramdisk = /usr/sbin/mkinitramfs

then running "apt-get install -f".  Poof!  Problem solved!

---

### Post by layback on 2007-04-13
Riiiight.  I have the same problem on edgy:

The following packages will be upgraded:
   linux-headers-2.6.17-11 (2.6.17.1-11.35 => 2.6.17.1-11.37)
   linux-headers-2.6.17-11-generic (2.6.17.1-11.35 => 2.6.17.1-11.37)
   linux-image-2.6.17-11-generic (2.6.17.1-11.35 => 2.6.17.1-11.37)

Unpacking replacement linux-image-2.6.17-11-generic ...
Running postrm hook /sbin/update-grub .
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.17-11-generic
Found kernel: /vmlinuz-2.6.17-10-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-headers-2.6.17-11 (2.6.17.1-11.37) ...

Setting up linux-headers-2.6.17-11-generic (2.6.17.1-11.37) ...
Setting up linux-image-2.6.17-11-generic (2.6.17.1-11.37) ...
Running depmod.
Finding valid ramdisk creators.
Failed to find suitable ramdisk generation tool for kernel version 
2.6.17-11-generic on running kernel 2.6.17-11-generic in /usr/sbin/mkinitramfs
dpkg: error processing linux-image-2.6.17-11-generic (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 linux-image-2.6.17-11-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

And you are right, removing the "ramdisk = /usr/sbin/mkinitramfs" from /etc/kernel-img.conf fixes the problem.  Unfortunately that line is essential to make my LUKs cryptoroot work properly and without it the system is not bootable :) 

Any other ideas?

---

