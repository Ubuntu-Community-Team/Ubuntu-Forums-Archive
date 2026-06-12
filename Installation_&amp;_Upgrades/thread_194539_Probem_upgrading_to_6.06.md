---
title: "Probem upgrading to 6.06"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by spaulson on 2006-06-11
I'm getting this error when running apt-get dist-upgrade -f

dpkg-divert: rename involves overwriting `/usr/bin/ldd' with
different file `/usr/bin/ldd.amd64', not allowed
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb (--unpack):
subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
/var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any Ideas how to resolve?

thx

---

### Post by spaulson on 2006-06-12
Solved this problem by renaming /usr/bin/ldd to /usr/bin/ldd.bak

This allowed the upgrade to continue.  System working now

---

