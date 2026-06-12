---
title: "building Karmic package ATI driver (64 bit) - Xfiles not found"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by starsprout on 2010-02-11
boy am I learning a lot today.

I'm on a new compaq with a Mobility Radeon 4200 series graphics driver and Ubuntu 9.10 64-bit.

I'm trying to compile a distro-specific build of the ATI Proprietery drivers from AMD, using the "--buildpkg Ubuntu/karmic" option but,

Package build failed!
Package build utility output:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.690-0ubuntu1


Some of the errors are about several "X"files (_XFlush,  _XReply, etc) being referenced that don't exist.

There's also one that says:
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.


Can anyone give me a clue?

---

