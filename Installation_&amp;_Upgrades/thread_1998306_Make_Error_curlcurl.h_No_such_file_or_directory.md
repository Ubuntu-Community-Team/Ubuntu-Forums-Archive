---
title: "Make Error: curl/curl.h: No such file or directory"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by triticale on 2012-06-06
I am trying to install a software called seqtools. When "make", I got messages:


make  all-am
make[1]: Entering directory `/home/peng/perlwork/alignment/seqtools-4.13.1'
gcc -DHAVE_CONFIG_H -I.  -pthread -D_REENTRANT -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I.   -g -O2 -MT libpfetch-utils.o -MD -MP -MF .deps/libpfetch-utils.Tpo -c -o libpfetch-utils.o `test -f './libpfetch/libpfetch-utils.c' || echo './'`./libpfetch/libpfetch-utils.c
In file included from ./libpfetch/libpfetch.h:41,
                 from ./libpfetch/libpfetch_P.h:39,
                 from ./libpfetch/libpfetch-utils.c:36:
./libpfetch/libcurlobject.h:41:23: error: curl/curl.h: No such file or directory
make[1]: *** [libpfetch-utils.o] Error 1
make[1]: Leaving directory `/home/peng/perlwork/alignment/seqtools-4.13.1'
make: *** [all] Error 2

Any suggestions? Thanks.

---

### Post by triticale on 2012-06-06
I got the answer. I installed ibcurl4-gnutls-dev and it is done.

---

