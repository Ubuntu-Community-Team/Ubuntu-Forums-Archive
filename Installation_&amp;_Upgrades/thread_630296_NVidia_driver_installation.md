---
title: "NVidia driver installation"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by nimeshchandran on 2007-12-03
hello guys i finally installed gutsy on my system using the alternate cd.. after that the os asked me to whether to enable restricted nvidia drivers and i enabled it... after i tried to install the nvidia-glx-new driver using the command sudo apt-get install nvidia-glx-new,,, but it didnt work.. the error that i got was

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  nvidia-settings nvidia-new-kernel-source
The following NEW packages will be installed:
  nvidia-glx-new
0 upgraded, 1 newly installed, 0 to remove and 45 not upgraded.
Need to get 0B/5014kB of archives.
After unpacking 15.2MB of additional disk space will be used.
(Reading database ... 84613 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.
deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4
-14.10_i386.deb (--unpack):
 trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-
xconfig
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

by the by my graphics card is geforce 7600GS AGP card...... so what should i do guys to install the drivers????

---

### Post by Ptero-4 on 2007-12-03
You have to uninstall nvidia-xconfig first. The nvidia-glx(legacy and new) package contains some of the stuff that is in the nvidia-xconfig package and so both conflict with each other.

---

