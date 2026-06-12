---
title: "xorg-video-abi-7.0"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by Naitsirhc Hsem on 2010-09-10
Hello, I am having trouble installing  xorg-video-abi-7.0 in Maverick, I can't find it anywhere.  any advice would be appreciated.  I am using a ati radeon 5770 and need it for a driver dependency

---

### Post by paul_in_london on 2012-01-14
```
paul@precise-64:~$ apt-cache show xserver-xorg-core
Package: xserver-xorg-core
Priority: optional
Section: x11
Installed-Size: 4059
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: amd64
Source: xorg-server
Version: 2:1.10.4-1ubuntu6
**[COLOR="Red"]Provides: xorg-input-abi-12, xorg-video-abi-10[/COLOR]**
Depends: xserver-common (>= 2:1.10.4-1ubuntu6), keyboard-configuration, udev (>= 149), libc6 (>= 2.8), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.5), libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0 (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.4.2)
Recommends: libgl1-mesa-dri (>= 7.10.2-4)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Conflicts: xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-4, xserver-xorg-input-7, xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5, xserver-xorg-video-6, xserver-xorg-video-nv, xserver-xorg-video-v4l
Breaks: libgl1-mesa-dri (<< 7.10.2-4), libgl1-mesa-dri-experimental (<< 7.10.2-4), libgl1-mesa-dri-no-multiarch, xserver-xorg-input-joystick (<= 1:1.5.0-3), xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4), xserver-xorg-input-tslib (<= 0.0.6-3), xserver-xorg-input-vmmouse (<= 1:12.6.5-4ubuntu2), xserver-xorg-input-wacom (<= 0.10.5+20100415-1), xserver-xorg-video-cyrix (<= 1:1.1.0-8), xserver-xorg-video-i810 (<< 2:2.4), xserver-xorg-video-imstt (<= 1:1.1.0-7), xserver-xorg-video-nsc (<= 1:2.8.3-4), xserver-xorg-video-sunbw2 (<= 1:1.1.0-5), xserver-xorg-video-vga (<= 1:4.1.0-8)
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.10.4-1ubuntu6_amd64.deb
Size: 1695808
MD5sum: 6d9af98c8fb2706e122ccdccb4583d1c
SHA1: f3ecae53a35a77ba572c1412e5fd8e8d9bd87442
SHA256: 2ac39409d2b60d381e5a1f53e72b5bd9307506afe2ad5d9d29c66edb19db5d7d
Description-en: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xserver module.
Description-md5: e3826a765918b79dee4b90ec97f9302c
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-mobile-desktop, kubuntu-mobile, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-core, ubuntustudio-desktop

Package: xserver-xorg-core
Source: xorg-server
Priority: optional
Section: x11
Installed-Size: 4007
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Version: 2:1.11.2.902+git20111209+server-1.11-branch.0ca8869e-0ubuntu0sarvatt
Recommends: libgl1-mesa-dri (>= 7.10.2-4)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Provides: xorg-input-abi-13, xorg-video-abi-11
Depends: xserver-common (>= 2:1.11.2.902+git20111209+server-1.11-branch.0ca8869e-0ubuntu0sarvatt), keyboard-configuration, udev (>= 149), libc6 (>= 2.8), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.5), libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.21.6), libudev0 (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.4.2)
Breaks: libgl1-mesa-dri (<< 7.10.2-4), libgl1-mesa-dri-experimental (<< 7.10.2-4), xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-4, xserver-xorg-input-7, xserver-xorg-input-joystick (<= 1:1.5.0-3), xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4), xserver-xorg-input-tslib (<= 0.0.6-3), xserver-xorg-input-vmmouse (<= 1:12.6.5-4ubuntu2), xserver-xorg-input-wacom (<= 0.10.5+20100415-1), xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5, xserver-xorg-video-6, xserver-xorg-video-cyrix (<= 1:1.1.0-8), xserver-xorg-video-i810 (<< 2:2.4), xserver-xorg-video-imstt (<= 1:1.1.0-7), xserver-xorg-video-nsc (<= 1:2.8.3-4), xserver-xorg-video-sunbw2 (<= 1:1.1.0-5), xserver-xorg-video-v4l (<< 1:0.2.0), xserver-xorg-video-vga (<= 1:4.1.0-8)
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.11.2.902+git20111209+server-1.11-branch.0ca8869e-0ubuntu0sarvatt_amd64.deb
Size: 1744492
MD5sum: 7c96f155ec0cf6d662fab46d831469c9
SHA1: c11ec80dfdf9f63ab454faa3254eeba28c66570d
Description-en: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xserver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

paul@precise-64:~$
```

```
paul@precise-64:~$ apt-cache search xorg-video-abi-11
xserver-xorg-core - Xorg X server - core server
```

Try the 2nd command with **xorg-video-abi-7.0** or whatever package you're interested in.

HTH

---

### Post by overdrank on 2012-01-14
Thanks for your input but the thread is over a year old. Thread closed.

---

