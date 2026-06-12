---
title: "libnet installation error"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by sawick61 on 2009-11-17
make[1]: Entering directory `/etc/libnet/lib'
gcc -O2 -Wall -Werror -Wno-unused -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -g -I../include -Iinclude -DTARGET_LINUX   -c -o core/config.o core/config.c
cc1: warnings being treated as errors
core/config.c: In function ‘__libnet_internal__seek_section’:
core/config.c:87: error: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
core/config.c: In function ‘__libnet_internal__get_setting’:
core/config.c:111: error: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
make[1]: *** [core/config.o] Error 1
make[1]: Leaving directory `/etc/libnet/lib'
make: *** [lib] Error 2

anyone know why i am getting this?

---

### Post by cojw8 on 2010-05-24
Got the same problem! Any solutions about it?

---

### Post by davidmohammed on 2010-05-24
suggest easiest way would be to install the binary package that has already been compiled for you -

see [here]("https://launchpad.net/ubuntu/+source/libnet") and click through to find the binary package for your version of ubuntu and processor

---

