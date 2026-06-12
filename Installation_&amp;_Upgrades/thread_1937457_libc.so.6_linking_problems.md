---
title: "libc.so.6 linking problems"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by pinkhairedcyn on 2012-03-07
I automatically upgraded libc.so.6 a couple of days ago, and now when I run some code I wrote, it crashes and I get the error message 

"relocation error:  symbol gettimeofday, version GLIB_2.0 not defined in file libc.so.6 with link time reference."

When I run ldd --version, it tells me I have glibc 2.13, so it looks like for some reason gcc is linking incorrectly.

I have tried recompiling many times, reinstall both libc.so.6 and gcc, upgrading to a newer version of Ubuntu, and uninstalling libglib2.0-0, and I still get this error.

Any insight on how to fix this would be amazing.

---

