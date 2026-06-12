---
title: "Xubuntu 8.04 Alternate fails md5sum hash check"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by capn_buzzcut on 2008-05-08
From what I can tell, Xubuntu 8.04 Alternate i386 will not pass an md5sum check.  I'm not talking about the iso image, that checks out fine.  Once the image is burned or extracted though, the resulting filesystem does not match the included md5sum.txt.  Here are the errors I get:

.\install\netboot\pxelinux.cfg\default ERROR: C:\Software\Linux\Xubuntu\xubuntu-8.04-alternate-i386\.\install\netboot\pxelinux.cfg\default does not exists.
.\install\netboot\pxelinux.0 ERROR: Checksum did not match.
.\pool\restricted\l\linux-restricted-modules-2.6.24\linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb ERROR: C:\Software\Linux\Xubuntu\xubuntu-8.04-alternate-i386\.\pool\restricted\l\linux-restricted-modules-2.6.24\linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.24\nic-restricted-modules-2.6.24-16-generic-di_2.6.24.12-16.34_i386.udeb ERROR: C:\Software\Linux\Xubuntu\xubuntu-8.04-alternate-i386\.\pool\restricted\l\linux-restricted-modules-2.6.24\nic-restricted-modules-2.6.24-16-generic-di_2.6.24.12-16.34_i386.udeb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.24\nic-restricted-firmware-2.6.24-16-generic-di_2.6.24.12-16.34_i386.udeb ERROR: C:\Software\Linux\Xubuntu\xubuntu-8.04-alternate-i386\.\pool\restricted\l\linux-restricted-modules-2.6.24\nic-restricted-firmware-2.6.24-16-generic-di_2.6.24.12-16.34_i386.udeb does not exists.
.\pool\main\l\linux\firewire-core-modules-2.6.24-16-generic-di_2.6.24-16.30_i386.udeb ERROR: C:\Software\Linux\Xubuntu\xubuntu-8.04-alternate-i386\.\pool\main\l\linux\firewire-core-modules-2.6.24-16-generic-di_2.6.24-16.30_i386.udeb does not exists.
.\pool\main\l\linux\pcmcia-storage-modules-2.6.24-16-generic-di_2.6.24-16.30_i386.udeb ERROR: C:\Software\Linux\Xubuntu\xubuntu-8.04-alternate-i386\.\pool\main\l\linux\pcmcia-storage-modules-2.6.24-16-generic-di_2.6.24-16.30_i386.udeb does not exists.
.\pool\main\x\xfree86-driver-synaptics\xserver-xorg-input-synaptics_0.14.7~git20070706-1ubuntu4_i386.deb ERROR: C:\Software\Linux\Xubuntu\xubuntu-8.04-alternate-i386\.\pool\main\x\xfree86-driver-synaptics\xserver-xorg-input-synaptics_0.14.7~git20070706-1ubuntu4_i386.deb does not exists.

I've downloaded the image several times using torrent and http, all from the mirror at "http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/".  The Desktop i386 image is fine, only the alternate seems to fail.  Anybody else get the same thing?

---

### Post by capn_buzzcut on 2008-05-08
Curiously, I just finished downloading the Ubuntu 8.04 Alternate i386, and get the same md5sum errors, on the same files.

---

