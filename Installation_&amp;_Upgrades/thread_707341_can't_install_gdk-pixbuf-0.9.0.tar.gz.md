---
title: "can't install gdk-pixbuf-0.9.0.tar.gz"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by jeryan on 2008-02-25
I am trying to  install  gdk-pixbuf-0.9.0 in ubuntu 7.10 but it doesn't work...& gave me this message:

--------------------------------------------
jerry@jerry-laptop:~/Desktop/gdk-pixbuf-0.9.0$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... configure: error: can not guess host type; you must specify one
---------------------------------------------

can anyone give me some ideas to work it out?  Please!:(

---

### Post by yabbadabbadont on 2008-02-26
gdk-pixbuf is in the repositories and can be installed using apt-get or synaptic.  Generally, you don't need to explicitly install it, as it will be pulled in automatically if you install something that needs it.  If you need the development version of it, then search for gdk-pixbuf in synaptic.  There should be another package that looks just like it, but ends in "-dev".  It will contain the development headers and such.

---

