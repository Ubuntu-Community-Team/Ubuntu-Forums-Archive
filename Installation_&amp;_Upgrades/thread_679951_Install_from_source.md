---
title: "Install from source"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by Jelmoh on 2008-01-27
I've downloaded a game and the tar.gz contains the source..
I've run the following commands
./configure (worked after installing some packages, build-essential was one of 'm)
make doesn't work... :S
This is what the terminal said to me:
> 
jelmer@jelmer-desktop:~/Desktop/gweled-0.7$ make
make  all-recursive
make[1]: Entering directory `/home/jelmer/Desktop/gweled-0.7'
Making all in src
make[2]: Entering directory `/home/jelmer/Desktop/gweled-0.7/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -DORBIT2=1 -pthread -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/gail-1.0 -I/usr/include/librsvg-2      -g -O2  -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
main.c:33:20: error: mikmod.h: No such file or directory
main.c:55: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c:56: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c: In function ‘main’:
main.c:265: error: ‘MikMod_errno’ undeclared (first use in this function)
main.c:265: error: (Each undeclared identifier is reported only once
main.c:265: error: for each function it appears in.)
main.c:309: error: ‘module’ undeclared (first use in this function)
main.c:312: error: ‘swap_sfx’ undeclared (first use in this function)
main.c:318: error: ‘click_sfx’ undeclared (first use in this function)
main.c: At top level:
main.c:374: fatal error: opening dependency file .deps/main.Tpo: Permission denied
compilation terminated.
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/jelmer/Desktop/gweled-0.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jelmer/Desktop/gweled-0.7'
make: *** [all] Error 2
jelmer@jelmer-desktop:~/Desktop/gweled-0.7$


How do I solve this, anyone?
I didn't try to find it in the repos..
But I'd really like this to be solved, I'll probably run into it some day with a program that isn't in the repos for sure!
Thank you very much in advance!

---

### Post by Seisen on 2008-01-27
Usually you can run make with superuser priveleges and it works but you can always try like "sudo make". Also this game is available in the repos.

---

### Post by Jelmoh on 2008-01-27
I've found this game in the repos later on.. :)
but that's what I said...
using sudo make has the same results

---

