---
title: "CodeLite install on debian 4.0"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by quasitr0n on 2008-07-02
Hello guys.
I want install IDE CodeLite. But I take next problem

```

debian:/home/quant# CodeLite
CodeLite: error while loading shared libraries: libcurl-gnutls.so.4: cannot open shared object file: No such file or directory
debian:/home/quant# ls /usr/lib/*curl*
/usr/lib/libcurl.so.3  /usr/lib/libcurl.so.3.0.0  /usr/lib/libcurl.so.4
debian:/home/quant# cat /etc/ld.so.conf.d/i486-linux-gnu.conf
# Multiarch support
/lib/i486-linux-gnu
/usr/lib/i486-linux-gnu
/usr/lib

```
Possible CodeLite not might found necessary library. Why?
I did hope your help.
Thank in adv.

---

### Post by eranif on 2008-09-16
Sorry to woke up a dead thread, but FWIW, CodeLite no longer requires libcurl (at least the development builds does not)


Eran

---

