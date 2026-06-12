---
title: "Is it possible to install via PXE using at ISO image"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by scaryant on 2007-01-06
Hi

I'm trying to help someone out and I'm trying to find out how to configure the boot image/install to use the Ubuntu ISO image rather than download install files from the net. I'm positive it can be done but I'm not sure how, I have a suspicion something needs to be changed in the \ubuntu-installer\i386\pxelinux.cfg\default file which contains the install commands used eg

> LABEL install
	kernel ubuntu-installer/i386/linux
	append vga=normal initrd=ubuntu-installer/i386/initrd.gz ramdisk_size=16417 root=/dev/ram rw  --

Anyone got any idea's?

---

### Post by dixonp on 2007-01-06
It is possible. I did it with the ubuntu-6.10-alternate-i386.iso image (I also ran into a GPG error, but found a workaround). See:

[http://ubuntuforums.org/showthread.php?t=332343](http://ubuntuforums.org/showthread.php?t=332343)

I think the GPG error is due to a bug in the installer (but nobody has replied to my bug theory yet).

---

