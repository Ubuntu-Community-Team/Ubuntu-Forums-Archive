---
title: "Issues with Intel Graphics"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by Aidan_Owen on 2015-09-05
I am trying to install my Intel Graphics Drivers, but when I run the installer I get this error:

```
Error running transaction: GDBus.Error:org.debian.apt.TransactionFailed: error-dep-resolution-failed: The following packages have unmet dependencies:


libgl1-mesa-dri: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed
libxatracker2: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed
xserver-xorg-video-intel: Depends: xorg-video-abi-18 but it is a virtual package

The following packages have unmet dependencies:


libgl1-mesa-dri: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed
libxatracker2: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed
xserver-xorg-video-intel: Depends: xorg-video-abi-18 but it is a virtual package




```

I have no idea how to fix this. Please help :P

It's also worth noting that in my Nvidia X Server Settings I cannot pick to use my Nvidia GPU - when I try it gives me an empty error box.

---

### Post by mc4man on 2015-09-06
If you are on 14.04 you can not use that Intel installer, it's for 14.10 only (and 14.10 is EOL or will be soon
If you are on 14.10 you've got the 14.04 version of libgcc1

---

