---
title: "Cannot download/update"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by JosephGarrison on 2010-01-28
When I try to download any application it fails. When I run the following command in the terminal this is what I get back.

joe@joe-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libplist0 amarok-common kdemultimedia-kio-plugins libkcddb4
  libqtscript4-core libusbmux0 libqtscript4-gui libqtscript4-uitools
  libqtscript4-sql libqtscript4-xml libconfig-tiny-perl libtag-extras1
  liblastfm0 amarok-utils libqtscript4-network
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libusbmuxd1 usbmuxd
The following NEW packages will be installed:
  libusbmuxd1 usbmuxd
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/37.2kB of archives.
After this operation, 205kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 151655 files and directories currently installed.)
Unpacking libusbmuxd1 (from .../libusbmuxd1_1.0.0-0ubuntu1~ppa2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libusbmuxd1_1.0.0-0ubuntu1~ppa2_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Unpacking usbmuxd (from .../usbmuxd_1.0.0-0ubuntu1~ppa2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/usbmuxd_1.0.0-0ubuntu1~ppa2_i386.deb (--unpack):
 trying to overwrite '/lib/udev/rules.d/85-usbmuxd.rules', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.0-0ubuntu1~ppa2_i386.deb
 /var/cache/apt/archives/usbmuxd_1.0.0-0ubuntu1~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe@joe-laptop:~$ 

How do I fix this?

---

### Post by arubislander on 2010-01-28
maybe you could try removing the packages that are suggested for autoremoval first?
```
sudo apt-get --purge autoremove
```

---

