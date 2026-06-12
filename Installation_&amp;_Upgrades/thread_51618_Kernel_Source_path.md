---
title: "Kernel Source path?"
date: 2005-07-24
forum: Installation &amp; Upgrades
---

### Post by Scombr0 on 2005-07-24
Where is the kernel source path? I'm trying to install an usb-driver and in the ./configure command gives an error telling me that can't find the kernel source path. 

Where is it? :(

Thank you :)

---

### Post by Xian on 2005-07-24
It is (if already installed) in the /usr/src path.

---

### Post by Scombr0 on 2005-07-24
I already checked that and i think it's not installed, how to install it?

---

### Post by az on 2005-07-24
Instead of the source, try just using the kernel headers.

The package for the stock kernel is linux-headers-2.6.10-5-386

Substitute the version if you are running a different kernel (like 686...)

It makes a symlink in /lib/modules/(version)/build so that the configure script should find it effortlessly.  If not, use /usr/src/linux-headers-2.6.10-5-386

---

