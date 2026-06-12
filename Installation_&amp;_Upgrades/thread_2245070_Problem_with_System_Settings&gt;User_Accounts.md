---
title: "Problem with System Settings&gt;User Accounts"
date: 2014-09-20
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2014-09-20
Since upgrading to 14.04.1 from 12.04.5, Applications>System Settings>User Accounts does not work.  In addition, I cannot close the Systems Settings window if I try to run User Accounts.  I believe the process that runs is unity-control-center.  I cannot end or kill that process.  Every time I kill the process, it spawns a new one.  How can I get this to work properly?  I am running 14.04.1 x64 Gnome-Flashback (Metacity).

---

### Post by cscj01 on 2014-09-21
I just noticed I have gnome-control-center and unity-control-center installed.  Could there be a conflict here?  If so, what should I remove?  It is my understanding that unity-control-center is Ubuntu's fork of gnome-control-center, and that they intend to move to ubuntu-control-center.

---

### Post by cscj01 on 2014-09-24
I ran the following command in a terminal:```
unity-control-center user-accounts
```I received the following message over and over```
libwayland_ltst-client.so.0: cannot open shared object file: No such file or directory
Failed to load module: /usr/lib/x86_64-linux-gnu/unity-control-center-1/panels/libuser-accounts.so
```Perhaps someone can help with this additional information.

---

### Post by cscj01 on 2014-09-24
I think libwayland_ltst-client.so.0 belongs to package libwayland-ltst-client0 which is a Precise package.  It seems this package was part of an HWE update to Precise.  The only problem is, I don't know why Applications>System Settings>User Accounts is calling this module.  I would have thought the upgrade from 12.04.5 to 14.04.1 would have sorted this out.  A little help here would be greatly appreciated.

---

### Post by cscj01 on 2014-09-24
Maybe this will help someone help me.```
dpkg -s libwayland-ltst-client0
Package: libwayland-ltst-client0
Status: deinstall ok config-files
Priority: optional
Section: libs
Installed-Size: 90
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: wayland-lts-trusty
Version: 1.4.0-1ubuntu1~precise1
Config-Version: 1.4.0-1ubuntu1~precise1
Replaces: libwayland0-lts-trusty (<< 1.1.0-1)
Depends: libc6 (>= 2.14), libffi6 (>= 3.0.4)
Pre-Depends: multiarch-support
Conflicts: libwayland0-lts-trusty (<< 1.1.0-1)
Description: wayland compositor infrastructure - client library
 Wayland is a protocol for a compositor to talk to its clients as well
 as a C library implementation of that protocol. The compositor can be
 a standalone display server running on Linux kernel modesetting and
 evdev input devices, an X application, or a wayland client
 itself. The clients can be traditional applications, X servers
 (rootless or fullscreen) or other display servers.
 .
 This package ships the library that implements the client side of
 the Wayland protocol.
Homepage: http://wayland.freedesktop.org/
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
```So what wayland packages should be in Trusty?  I have the following installed:> [LIST=1]
[*]libwayland-egl1-mesa
[*]libwayland-client0
[*]libwayland-server0
[*]libwayland-dev
[*]libwayland-cursor0
[*]
[/LIST]

---

### Post by cscj01 on 2014-09-30
Surely someone has some thoughts on why ```
unity-control-center user-accounts
``` is calling a Precise package?

---

