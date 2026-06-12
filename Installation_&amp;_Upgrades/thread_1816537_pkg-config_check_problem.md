---
title: "pkg-config check problem"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by medha6 on 2011-08-02
I have Ubuntu 10.04 64 bit (just upgraded today)!

I am trying to compile an opensource software and its configure script keeps failing in pkg-config. For example, pkg-config fails on openssl, although openssl libraries are present in /usr/lib and /lib.

Little bit search on web told me that for pkg-config to find the status and info of packages *.pc files of respective libraries have to be there under "PKG_CONFIG_PATH" which defaults to /usr/lib/pkgconfig/.

I tried to manually put openssl.pc there which i could grab from the web, but still for many other packages/libraries, it's the same trouble, e.g. PCRE package's *.pc file under /usr/lib/pkgconfig is missing as well.

Am I missing something in the Ubuntu upgrade?

How can I resolve this problem asap?

---

