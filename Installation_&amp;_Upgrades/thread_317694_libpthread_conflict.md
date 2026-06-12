---
title: "libpthread conflict?"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by recupero on 2006-12-12
libpthread-dev cannot be installed due to overlap with other libs.
The error causes libpthread-dev not to be installed at all.

E: /var/cache/apt/archives/libpthread-dev_2.0.7-2ubuntu2_i386.deb: trying to overwrite `/usr/include/pthread.h', which is also in package libc6-dev

I am using the latest Edgy distro.

---

### Post by lordmule on 2007-04-04
I also have this problem for compiling source. My workaround is to compile my files by pointing LD_LIBRARY_PATH to the binaries...not happy.

Why would libc6-dev include a pthread.h without the development files anyway? seems wrong if they make it a half dependency. This is what preprocessor #ifdef's are good for.

---

