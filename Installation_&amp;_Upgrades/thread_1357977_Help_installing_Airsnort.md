---
title: "Help installing Airsnort?"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by wigglestix on 2009-12-17
I am new to linx and i have been having some problems installing .tar.gz files.  I am trying to install airsnort and when i run ./configure and it works fine but when i run make i get this error.

  /bin/bash ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/home/kristian/src/airsnort-0.2.7'
Making all in src
make[2]: Entering directory `/home/kristian/src/airsnort-0.2.7/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
    then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
callbacks.c:9:18: error: pcap.h: No such file or directory
In file included from callbacks.c:24:
PacketSource.h:149: error: expected specifier-qualifier-list before ‘pcap_t’
PacketSource.h:174: warning: ‘struct pcap_pkthdr’ declared inside parameter list
PacketSource.h:174: warning: its scope is only this definition or declaration, which is probably not what you want
PacketSource.h:175: warning: ‘struct pcap_pkthdr’ declared inside parameter list
callbacks.c:93: error: ‘PCAP_ERRBUF_SIZE’ undeclared here (not in a function)
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/home/kristian/src/airsnort-0.2.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kristian/src/airsnort-0.2.7'
make: *** [all] Error 2

---

### Post by theorka on 2011-01-30
I had that same problem (still haven't got airsnort to run).
This fix my problem;

sudo apt-get install libpcap0.8-dev2

---

