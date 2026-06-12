---
title: "How come I can't configure, make or make install?"
date: 2005-10-09
forum: Installation &amp; Upgrades
---

### Post by dreamer_nights on 2005-10-09
I can get configure to work on rare occasions, but it's make and make install that won;t work at all. What files am i missing?

---

### Post by Leif on 2005-10-09
sudo apt-get install build-essentials

---

### Post by dreamer_nights on 2005-10-09
Didnt work

---

### Post by Leif on 2005-10-09
sorry, should be sudo apt-get install build-essential

---

### Post by dreamer_nights on 2005-10-09
Already installed & updated. What else am i missing?

---

### Post by Leif on 2005-10-09
what error message do you get ?

---

### Post by dreamer_nights on 2005-10-09
transparentdreams@ubuntu:~/Desktop/Gforecast-0.4$ make
Making all in macros
make[1]: Entering directory `/home/transparentdreams/Desktop/Gforecast-0.4/macro s'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/transparentdreams/Desktop/Gforecast-0.4/macros '
Making all in po
make[1]: Entering directory `/home/transparentdreams/Desktop/Gforecast-0.4/po'
make[1]: Leaving directory `/home/transparentdreams/Desktop/Gforecast-0.4/po'
Making all in intl
make[1]: Entering directory `/home/transparentdreams/Desktop/Gforecast-0.4/intl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/transparentdreams/Desktop/Gforecast-0.4/intl'
make[1]: Entering directory `/home/transparentdreams/Desktop/Gforecast-0.4'
gcc -DPACKAGE=\"Gforecast\" -DVERSION=\"0.4\" -DSTDC_HEADERS=1 -DHAVE_X11_SM_SML IB_H=1 -DHAVE_LIBSM=1 -DHAVE_LIBGNOMEUI=1 -DHAVE_ALLOCA_H=1 -DHAVE_ALLOCA=1 -DHA VE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_ARGZ_H=1 -DHAVE_LIMITS_H =1 -DHAVE_LOCALE_H=1 -DHAVE_NL_TYPES_H=1 -DHAVE_MALLOC_H=1 -DHAVE_STRING_H=1 -DH AVE_UNISTD_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_GETCWD=1 -DHAVE_MUNMAP=1 -DHAVE_PUTEN V=1 -DHAVE_SETENV=1 -DHAVE_SETLOCALE=1 -DHAVE_STRCHR=1 -DHAVE_STRCASECMP=1 -DHAV E_STRDUP=1 -DHAVE___ARGZ_COUNT=1 -DHAVE___ARGZ_STRINGIFY=1 -DHAVE___ARGZ_NEXT=1 -DHAVE_STPCPY=1 -DHAVE_STPCPY=1 -DHAVE_LC_MESSAGES=1 -DENABLE_NLS=1 -DHAVE_GETTE XT=1 -DHAVE_DCGETTEXT=1  -I. -I.  -I. -I. -I/usr/local/include -I/usr/include/gn ome-1.0 -DNEED_GNOMESUPPORT_H -I/usr/lib/gnome-libs/include -I/usr/include/glib- 1.2 -I/usr/lib/glib/include -I/usr/include/orbit-1.0 -I/usr/include/gtk-1.2  -I/ usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  -g -O2 -Wal l -Wunused  -c Gforecast.c
Gforecast.c:9:27: applet-widget.h: No such file or directory
Gforecast.c:113: error: syntax error before '*' token
Gforecast.c: In function `apply_config':
Gforecast.c:168: warning: implicit declaration of function `applet_widget_sync_c onfig'
Gforecast.c:168: warning: implicit declaration of function `APPLET_WIDGET'
Gforecast.c: At top level:
Gforecast.c:174: error: syntax error before '*' token
Gforecast.c: In function `configuration_dialog':
Gforecast.c:212: error: `data' undeclared (first use in this function)
Gforecast.c:212: error: (Each undeclared identifier is reported only once
Gforecast.c:212: error: for each function it appears in.)
Gforecast.c: At top level:
Gforecast.c:217: error: syntax error before '*' token
Gforecast.c:232: error: syntax error before '*' token
Gforecast.c: In function `main':
Gforecast.c:247: warning: implicit declaration of function `applet_widget_init'
Gforecast.c:249: warning: implicit declaration of function `applet_widget_new'
Gforecast.c:249: warning: assignment makes pointer from integer without a cast
Gforecast.c:255: error: invalid type argument of `->'
Gforecast.c:266: warning: implicit declaration of function `applet_widget_get_pa nel_pixel_size'
Gforecast.c:269: warning: implicit declaration of function `applet_widget_add'
Gforecast.c:282: warning: implicit declaration of function `applet_widget_regist er_stock_callback'
Gforecast.c:314: warning: implicit declaration of function `applet_widget_gtk_ma in'
make[1]: *** [Gforecast.o] Error 1
make[1]: Leaving directory `/home/transparentdreams/Desktop/Gforecast-0.4'
make: *** [all-recursive] Error 1
transparentdreams@ubuntu:~/Desktop/Gforecast-0.4$ sudo apt-get install build-essentials
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials
transparentdreams@ubuntu:~/Desktop/Gforecast-0.4$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
transparentdreams@ubuntu:~/Desktop/Gforecast-0.4$

---

### Post by Leif on 2005-10-09
hmm, not sure why that is. there is an rpm for it at the site, which you can do "sudo alien foo.rpm" "sudo dpkg -i foo.deb" to.

---

