---
title: "Torrent flux, Python 2.6"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by quietas on 2009-03-29
Torrentflux has Python issues. I'm not sure if this relates to the borked issue though as I seem to have a higher version number.

```
culley@server:~$ apt-cache show python2.6
Package: python2.6
Priority: important
Section: python
Installed-Size: 10004
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Architecture: amd64
Version: 2.6.1-1ubuntu7
Provides: python2.6-celementtree, python2.6-cjkcodecs, python2.6-ctypes, python2.6-elementtree, python2.6-wsgiref
Depends: python2.6-minimal (= 2.6.1-1ubuntu7), mime-support, libbz2-1.0, libc6 (>= 2.7), libdb4.7, libncursesw5 (>= 5.6+20071006-3), libreadline5 (>= 5.2), libsqlite3-0 (>= 3.6.10), libssl0.9.8 (>= 0.9.8f-5)
Suggests: python2.6-doc, python2.6-profiler, binutils
Filename: pool/main/p/python2.6/python2.6_2.6.1-1ubuntu7_amd64.deb
Size: 2703990
MD5sum: 1f4213dde29894a8854949280eea01ae
SHA1: 2676a9116ef97f7ebb8e8c1266f2fc1e421ad397
SHA256: 082e68b360644d0a1b7c2b377faaa2bd30d25c2887fee1f296c313f35ee59aa8
Description: An interactive high-level object-oriented language (version 2.6)
 Version 2.6 of the high-level, interactive object oriented language,
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
Python-Version: 2.6
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: minimal, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend

```

The error I get is in the apache.log file.
```
/var/lib/python-support/python2.6/BitTornado/__init__.py:8: DeprecationWarning: the sha module is deprecated; use the hashlib module instead

```

Server stats:
```
Linux server 2.6.28-11-server #37-Ubuntu SMP Mon Mar 23 17:33:24 UTC 2009 x86_64 GNU/Linux

Distributor ID:	Ubuntu
Description:	Ubuntu jaunty (development branch)
Release:	9.04
Codename:	jaunty

processor	: 0
vendor_id	: GenuineIntel
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz		: 2800.000
bogomips	: 5999.26

processor	: 1
vendor_id	: GenuineIntel
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz		: 2800.000
bogomips	: 6000.16

```

---

### Post by quietas on 2009-04-03
TorrentFlux is running and will load correctly with the more recent Python updates. I am still having problems with some torrent sites though, Piratebay in particular.

It seems from the error I am getting (quoted above in apache2/error.log) that the error stems from the python-crypto package. There is even a possible fix from what I have read.

[https://bugs.edge.launchpad.net/ubuntu/+source/python-crypto/+bug/337073](https://bugs.edge.launchpad.net/ubuntu/+source/python-crypto/+bug/337073)

Can someone look in to this and get it rolled in soon? (or is it already?)

---

### Post by quietas on 2009-04-05
Looks like the Python update this evening fixed it.

---

