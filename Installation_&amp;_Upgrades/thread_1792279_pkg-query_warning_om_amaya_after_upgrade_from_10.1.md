---
title: "pkg-query warning om amaya after upgrade from 10.10 to 11.04"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2011-06-28
After upgrading from 10.10 to 11.04 I get the following warning

/etc/cron.daily/man-db:
dpkg-query: warning: parsing file '/var/lib/dpkg/available' near line 59383 package 'amaya':
 error in Version string 'wx-11.3.1-1': version number does not start with digit

Following is an extract of the file
------------------------------------------------

Package: amaya
Priority: optional
Section: web
Installed-Size: 53548
Maintainer: Laurent Carcone <carcone@w3.org>
Architecture: amd64
Version: wx-11.3.1-1
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7), libexpat1 (>= 1.95.8), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.14.1), libpango1.0-0 (>= 1.21.6), libraptor1 (>= 1.4.16), libsm6, libssl0.9.8 (>= 0.9.8f-5), libstdc++6 (>= 4.2.1), libx11-6, libxext6, libxinerama1, zlib1g (>= 1:1.1.4)
Size: 21407136
Description: XHTML, MathML, and SVG editor from w3.org
 Amaya is a Web editor, i.e. a tool used to create and update documents
 directly on the Web. Browsing features are seamlessly integrated with
 the editing and remote access features in a uniform environment.
 Amaya is based on the Thot toolkit developed at INRIA.
------------------------------------------------

Question is, how to fix this?

---

### Post by lister171254 on 2011-07-06
Bump.

I don't have amaya installed, so not sure why the package is being checked in the first place

---

