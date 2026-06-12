---
title: "Broken package"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Shadow12313 on 2010-04-03
When ever I try to install or remove a program it gives me an error saying there is a broken package.

I tried sudo apt-get install -f but it returned an error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 python-beagle libtasn1-3-dev libusbmuxd-dev libgpg-error-dev
  nvidia-185-libvdpau nvidia-185-kernel-source libgtksourceview1.0-0
  libgcrypt11-dev libopenjpeg2 libsqlite3-dev libass3 python-gtksourceview
  libgupnp-av-1.0-1 sdparm libx264-67 libcelt0 libgnutls-dev
  libimobiledevice-dev libgtksourceview-common libxml2-dev libffado1
  libxml++2.6-2 libusb-1.0-0-dev libplist-dev libconfig-tiny-perl
  python-nautilusburn libnautilus-burn4 libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine1.2
The following NEW packages will be installed:
  wine1.2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/9,596kB of archives.
After this operation, 81.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: regarding .../wine1.2_1.1.41-0ubuntu2_i386.deb containing wine1.2:
 wine1.2 conflicts with wine (<< 1.2)
  wine (version 1.1.41-0ubuntu2) is present and unpacked but not configured.
dpkg: error processing /var/cache/apt/archives/wine1.2_1.1.41-0ubuntu2_i386.deb (--unpack):
 conflicting packages - not installing wine1.2
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.2_1.1.41-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?
Thank-you in advance!

---

### Post by Naitsirhc Hsem on 2010-04-03
open up synaptec and click on the filters and check broken packages.  select remove on the broken one and hit apply.

---

### Post by Naitsirhc Hsem on 2010-04-03
also try removing the old version of wine

---

