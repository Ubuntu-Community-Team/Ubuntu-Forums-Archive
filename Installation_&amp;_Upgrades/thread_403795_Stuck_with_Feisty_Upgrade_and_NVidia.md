---
title: "Stuck with Feisty Upgrade and NVidia"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by W@LT on 2007-04-07
Hi
I have upgraded to Feisty and lost my NVidia Card Drivers

I have tried all the suggested fixes but can seem to get it back working

Nvidia GeForce 7600

If I try the sudo apt-get install nvidia-glx

I get the following

Can you help?

zeus@zeus-desktop:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python2.4-dev knewsticker-scripts module-assistant xserver-xorg-dev
  libgbf-1-0 libmagick++9c2a libkexif1 libburn2 libmono-system-runtime2.0-cil
  libapr0 mesa-common-dev libclamav1 ndiswrapper-utils libossp-uuid13 libsvn0
  libexif-dev libgphoto2-2-dev librpcsecgss2 libmono-sharpzip0.6-cil
  libglu1-mesa-dev libwv-1.2-1 libxt-dev libxine-main1 libxml1
  python-glade-1.2 libgbf-1-common libtunepimp3 rcs libgdk-pixbuf2 docker
  libdbus-glib-1-dev python-gtk-1.2 python-wxversion libgl1-mesa-dev
  mono-classlib-2.0 libpq4 libmono-system-runtime1.0-cil python-pyrss2gen
  python-wxgtk2.6 libisofs2 libglade0 dh-make libberylsettings-dev
  libnews-nntpclient-perl ndiswrapper-utils-1.1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4833kB of archives.
After unpacking 14.8MB of additional disk space will be used.
(Reading database ... 301952 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.9755+2.6.20.4-14.15_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-legacy'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.9755+2.6.20.4-14.15_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.9755+2.6.20.4-14.15_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
zeus@zeus-desktop:~$

---

### Post by fordfan753 on 2007-04-07
Do you still have the legacy nvidia driver installed? If so uninstall it, then try to install nvidia-glx again.

---

