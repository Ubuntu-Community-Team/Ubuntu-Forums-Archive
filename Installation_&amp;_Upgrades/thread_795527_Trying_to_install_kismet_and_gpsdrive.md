---
title: "Trying to install kismet and gpsdrive"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by chango77745 on 2008-05-15
While trying to install kismet as I type the command *./configure* I get this error message at the end,
"configure: WARNING: Unable to find libncurses
checking for initscr in -lcurses... no
configure: error: Unable to find libncurses or libcurses

I checked to make sure that I have libncurses installed on the synaptic package manager and it says that it is installed. 

Also, while I am trying to install gpsdrive I get this error message while trying to *make* it

"make  all-recursive
make[1]: Entering directory `/home/evan/Desktop/gpsdrive-2.10pre4'
Making all in src
make[2]: Entering directory `/home/evan/Desktop/gpsdrive-2.10pre4/src'
make[3]: Entering directory `/home/evan/Desktop/gpsdrive-2.10pre4/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DFRIENDSSERVERVERSION=\"2\"    -I/usr/include/ -I/usr/local/include -I/opt/boost_1_35/include/boost-1_35 -I/usr/local/include/freetype2 -I/usr/include/freetype2 -I. -L/usr/local/lib -I. -I. -I..     -g -O2 -g -Wall -Wno-format-y2k -pipe  -DHAVE_GTK   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libart-2.0   -I/usr/include/libxml2   -DHAVE_CAIRO -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12    -Imysql  -MT gpsdrive.o -MD -MP -MF ".deps/gpsdrive.Tpo" -c -o gpsdrive.o gpsdrive.c; \
        then mv -f ".deps/gpsdrive.Tpo" ".deps/gpsdrive.Po"; else rm -f ".deps/gpsdrive.Tpo"; exit 1; fi
In file included from gpsdrive.c:78:
./gpsdrive_config.h:35:25: error: mysql/mysql.h: No such file or directory
In file included from gpsdrive.c:95:
gpsdrive.h:31:25: error: mysql/mysql.h: No such file or directory
In file included from gpsdrive.c:95:
gpsdrive.h:242: error: expected ‘)’ before ‘*’ token
gpsdrive.h:243: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gpsdrive.h:244: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gpsdrive.h:251: error: expected ‘)’ before ‘*’ token
gpsdrive.h:252: error: expected ‘)’ before ‘*’ token
gpsdrive.h:253: error: expected declaration specifiers or ‘...’ before ‘*’ token
gpsdrive.h:253: error: expected ‘)’ before ‘*’ token
gpsdrive.h:254: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gpsdrive.h:255: error: expected declaration specifiers or ‘...’ before ‘*’ token
gpsdrive.h:255: error: expected ‘)’ before ‘*’ token
gpsdrive.h:256: error: expected ‘)’ before ‘*’ token
gpsdrive.h:257: error: expected declaration specifiers or ‘...’ before ‘*’ token
gpsdrive.h:257: error: expected ‘)’ before ‘*’ token
make[3]: *** [gpsdrive.o] Error 1
make[3]: Leaving directory `/home/evan/Desktop/gpsdrive-2.10pre4/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/evan/Desktop/gpsdrive-2.10pre4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/evan/Desktop/gpsdrive-2.10pre4'
make: *** [all] Error 2"

Someone please help me out on this!! Thanks so much

---

