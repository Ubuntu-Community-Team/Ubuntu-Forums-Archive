---
title: "short read on buffer copy for backend dpkg-deb"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by uberkerNoob on 2010-12-13
OKay first sorry for being so new but I keep getting the following errors, I've had similar errors when upgrading ubuntu in the past and gone back to Windows.... (shudder) anyways this is the response I get;

> Unpacking linux-image-2.6.35-23-generic (from .../linux-image-2.6.35-23-generic_2.6.35-23.41_amd64.deb) ...
Done.
dpkg-deb (subprocess): data: internal bzip2 read error 'DATA_ERROR'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.35-23-generic_2.6.35-23.41_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./lib/modules/2.6.35-23-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko'
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.35-23-generic_2.6.35-23.41_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Thanks ever so much

---

### Post by dunnemann on 2011-01-06
Take a look this: [http://ubuntuforums.org/showthread.php?t=1612598](http://ubuntuforums.org/showthread.php?t=1612598)
maybe helps you

---

