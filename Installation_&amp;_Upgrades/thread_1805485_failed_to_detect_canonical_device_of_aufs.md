---
title: "failed to detect canonical device of aufs"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by milos84 on 2011-07-16
I'm using Ubuntu 11.04 usb installation. When I tried to update from terminal I got this message "failed to detect canonical device of aufs". I have Fujitsu Siemens V5505 (Intel processor T5550, Intel 965 chip set and other hardware is pretty standard as on any other Fujitsu).


Copy-Paste from terminal:

[HTML]Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
cryptsetup: WARNING: failed to detect canonical device of aufs
cryptsetup: WARNING: could not determine root device from /etc/fstab
lzma: Encoder error: -2147467259
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-support ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)[/HTML]Any suggestion?

---

### Post by dino99 on 2011-07-16
you are not alone :(, you hit this one:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/691985](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/691985)

[https://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions](https://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions)

---

