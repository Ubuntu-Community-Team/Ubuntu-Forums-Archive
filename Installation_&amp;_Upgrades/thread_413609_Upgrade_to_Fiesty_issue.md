---
title: "Upgrade to Fiesty issue"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Darkdelusions on 2007-04-19
Well everything appears to be ok however expect the nividia restricted stuff. If i am reading this correctly the upgrade is trying to install an older version of the nvidia stuff but I have the latest and greatest nivida drivers install am i correct on this? 

```

E: /var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb:
subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb:
conflicting packages - not installing nvidia-glx
E: /var/cache/apt/archives/libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb:
conflicting packages - not installing libgl1-mesa-dev
E: /var/cache/apt/archives/mesa-common-dev_6.5.2-3ubuntu7_all.deb:
conflicting packages - not installing mesa-common-dev

(Reading database ... 162936 files and directories currently installed.)
Preparing to replace nvidia-glx-dev 1.0.9755 (using
.../nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so to
/usr/lib/nvidia/libGL.so.xlibmesa by nvidia-glx-dev' clashes with
`diversion of /usr/lib/libGL.so to /usr/lib/nvidia/libGL.so.xlibmesa
by nvidia-glx'
dpkg: error processing
/var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb
(--unpack):
 subprocess pre-installation script returned error exit status 2
dpkg: regarding .../libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb containing
libgl1-mesa-dev:
 libgl1-mesa-dev conflicts with libgl-dev
 nvidia-glx-dev provides libgl-dev and is installed.
dpkg: error processing
/var/cache/apt/archives/libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb
(--unpack):
 conflicting packages - not installing libgl1-mesa-dev
dpkg: regarding .../mesa-common-dev_6.5.2-3ubuntu7_all.deb containing
mesa-common-dev:
 nvidia-glx-dev conflicts with mesa-common-dev
 mesa-common-dev (version 6.5.2-3ubuntu7) is to be installed.
dpkg: error processing
/var/cache/apt/archives/mesa-common-dev_6.5.2-3ubuntu7_all.deb
(--unpack):
 conflicting packages - not installing mesa-common-dev
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb
 /var/cache/apt/archives/libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb
 /var/cache/apt/archives/mesa-common-dev_6.5.2-3ubuntu7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```

---

