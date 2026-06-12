---
title: "error while loading shared libraries: libm.so.6"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by Strelock on 2006-11-24
Hi folks,

I'm installing a in-house developed software on Ubuntu 6.10 and I got "error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory". 

Same installation works fine on Redhat. 

locate libm.so.6 returns:
/lib/libm.so.6
/lib/tls/i686/cmov/libm.so.6

Both are links to libm-2.4.so which exists in both folders...

I have absolutely no idea what's the problem...

---

### Post by actuary09 on 2007-10-25
I was trying to install IBM informix sQL and 4GL and sot a similar message -- could not find  libm.so.6.

Where can I get a copy?

---

