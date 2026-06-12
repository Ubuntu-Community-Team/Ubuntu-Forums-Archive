---
title: "How to install Ubuntu on ibm x41 (without CDROM)"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by harveyfly on 2006-07-17
Here's the story:
I have no CD drive for the laptop, I can only install by my 256MB flash drive or external usb harddisk. Since the 256MB flash drive is not big enough to hold the Ubuntu live cd content and I am not familiar with installing with minimal packages. My only choice would be the external usb harddisk.
I used syslinux to enable booting to the Fat16 partition of the usb harddisk, however the installation stops forever at "Uncompressing linux, OK, boot the kernel". I have googled the net and still not come out with any solution. Any body has idea of this?
And I also want to know if there's any other way for me to install Ubuntu on the cdromless laptop?

Thanks a lot

---

### Post by erjohan on 2006-07-17
Hi I'm using an X40 trying todo the same, but I use PXE boot. I've done it with breezy and hoary,  and right now with dapper. 

What I do is;
Download these
* [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux)
* [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz)

and make them boot from your flash drive. Sadly it doesn't always work, flashdrives may boot on one computer but not on another..

here is an guide.
[http://www.gentoo.org/doc/en/liveusb.xml](http://www.gentoo.org/doc/en/liveusb.xml)

---

