---
title: "Glibc_2.8?"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by dgohn on 2009-12-02
A user on my server is getting the following error:


./netmush: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.8' not found (required
 by ./netmush)


I am using Ubuntu Server (i386)


I have tried updating libc, glibc, and it just tells me this is the newest version.  Any ideas what I am missing?  Thanks in advance

---

### Post by dgohn on 2009-12-03
*bump*

---

### Post by dgohn on 2009-12-03
Disregard.  The user did not do a ./configure after moving his files over.  This fixed the problem and let him execute his startup script.

---

