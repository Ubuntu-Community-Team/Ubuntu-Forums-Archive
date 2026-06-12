---
title: "Trying to install airsnort"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by chango77745 on 2008-05-15
I am trying to install airsnort, but I keep getting this error when I use the "make" command. I did do the ./configure command first.

"evan@evan-laptop:~/Desktop/airsnort-0.2.7e$ make
make  all-recursive
make[1]: Entering directory `/home/evan/Desktop/airsnort-0.2.7e'
Making all in src
make[2]: Entering directory `/home/evan/Desktop/airsnort-0.2.7e/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2 -MT support.o -MD -MP -MF ".deps/support.Tpo" -c -o support.o support.c; \
        then mv -f ".deps/support.Tpo" ".deps/support.Po"; else rm -f ".deps/support.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2 -MT interface.o -MD -MP -MF ".deps/interface.Tpo" -c -o interface.o interface.c; \
        then mv -f ".deps/interface.Tpo" ".deps/interface.Po"; else rm -f ".deps/interface.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
        then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
In file included from PacketSource.h:31,
                 from callbacks.c:24:
/usr/include/linux/wireless.h:650: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:663: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:677: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:688: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:704: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:717: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:744: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:806: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:820: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:834: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:842: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:851: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:863: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:886: error: ‘IFNAMSIZ’ undeclared here (not in a function)
/usr/include/linux/wireless.h:901: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:945: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1046: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1064: error: expected specifier-qualifier-list before ‘__u16’
callbacks.c: In function ‘fillDeviceList’:
callbacks.c:121: error: storage size of ‘ir’ isn’t known
callbacks.c:129: error: ‘IFF_LOOPBACK’ undeclared (first use in this function)
callbacks.c:129: error: (Each undeclared identifier is reported only once
callbacks.c:129: error: for each function it appears in.)
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/home/evan/Desktop/airsnort-0.2.7e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/evan/Desktop/airsnort-0.2.7e'
make: *** [all] Error 2"

---

