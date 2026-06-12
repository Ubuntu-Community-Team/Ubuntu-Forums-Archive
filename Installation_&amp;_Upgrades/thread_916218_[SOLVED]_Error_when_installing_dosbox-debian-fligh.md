---
title: "[SOLVED] Error when installing dosbox-debian-flightgear"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by Dyffo on 2008-09-10
When trying to install dos box, debian and flightgear this error
appears. I am using UBUNTU 8.04. Any ideas ??

 Verification on package /var/cache/apt/archives/libmikmod2_3.1.11-a-6ubuntu3_i386.deb failed!
Authenticating /var/cache/apt/archives/libsdl-sound1.2_1.0.1-12build2_i386.deb ...
debsig: Origin Signature check failed. This deb might not be signed.

dpkg: error processing /var/cache/apt/archives/libsdl-sound1.2_1.0.1-12build2_i386.deb (--unpack):
 Verification on package /var/cache/apt/archives/libsdl-sound1.2_1.0.1-12build2_i386.deb failed!
Authenticating /var/cache/apt/archives/dosbox_0.72-1.1build1_i386.deb ...
debsig: Origin Signature check failed. This deb might not be signed.

dpkg: error processing /var/cache/apt/archives/dosbox_0.72-1.1build1_i386.deb (--unpack):
 Verification on package /var/cache/apt/archives/dosbox_0.72-1.1build1_i386.deb failed!
Errors were encountered while processing:
 /var/cache/apt/archives/libsdl-net1.2_1.2.7-2_i386.deb
 /var/cache/apt/archives/libmikmod2_3.1.11-a-6ubuntu3_i386.deb
 /var/cache/apt/archives/libsdl-sound1.2_1.0.1-12build2_i386.deb
 /var/cache/apt/archives/dosbox_0.72-1.1build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


ProblemType: Package
Architecture: i386
Date: Sat Sep  6 22:54:21 2008
Dependencies:
 
DistroRelease: Ubuntu 8.04
ErrorMessage: Verification on package /var/cache/apt/archives/libsdl-sound1.2_1.0.1-12build2_i386.deb failed!
Package: libsdl-sound1.2 None [modified: /var/lib/dpkg/info/libsdl-sound1.2.list]
PackageArchitecture: i386
SourcePackage: libsdl-sound1.2
Title: package libsdl-sound1.2 None [modified: /var/lib/dpkg/info/libsdl-sound1.2.list] failed to install/upgrade: Verification on package /var/cache/apt/archives/libsdl-sound1.2_1.0.1-12build2_i386.deb failed!
Uname: Linux 2.6.24-21-generic i686

---

