---
title: "problem with xulrunner"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by djpalshikar on 2010-11-17
I am running Ubuntu LTS, upgraded to Meerkat .
I was having problems with ubuntu help and other programs depending on xulrunner-1.9.2.
I get this message each time i use apt-get:
Setting up xulrunner-1.9.2 (1.9.2.12+build1+nobinonly-0ubuntu0.10.10.1) ...
/usr/lib/xulrunner-1.9.2.12/xulrunner-bin: symbol lookup error: /usr/lib/xulrunner-1.9.2.12**/libxul.so: undefined symbol: cairo_xlib_surface_create_with_xrender_format**
dpkg: error processing xulrunner-1.9.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 xulrunner-1.9.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried reinstalled libcairo2 but it made no difference. Surprisingly I have on dual boot a freshly installed Ubuntu 10.10, which works just fine..
this has really been troubling me for a while, Please help
thanks in advance

---

### Post by djpalshikar on 2010-11-23
anyone who could help..?

---

