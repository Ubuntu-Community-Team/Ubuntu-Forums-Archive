---
title: "GTK pango and pkg-config"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by pashby on 2005-11-27
Hello all

I am new to the Linux world but not new to Computing.

I have been puzzling for a long while now on why I can't get any sense out of pkg-config.

I am trying to install a later version of GTK and it keeps throwing dependecy errors of the type

checking for pkg-config... /home/peter/mono-1.1.10/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES_CFLAGS...
checking for BASE_DEPENDENCIES_LIBS...
Package pango was not found in the pkg-config search path.
Perhaps you should add the directory containing `pango.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pango' found
configure: error: Package requirements (glib-2.0 >= 2.6.0    atk >= 1.0.1    pango >= 1.8.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

I have successfully installed pango 1.8.2 and atk 1.10.1 with no obvious errors but pkg-config will not find them!
I have even installed pkg-config 0.19 but to no avail.

I must admit that this experience is souring my outlook on Linux.

Can someone offer help - I have trolled the net but find little of help.

Regards to all 
Peter

---

### Post by basscad on 2005-12-15
[QUOTE=pashby]Hello all

I am new to the Linux world but not new to Computing.

I have been puzzling for a long while now on why I can't get any sense out of pkg-config.

I am trying to install a later version of GTK and it keeps throwing dependecy errors of the type

checking for pkg-config... /home/peter/mono-1.1.10/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES_CFLAGS...
checking for BASE_DEPENDENCIES_LIBS...
Package pango was not found in the pkg-config search path.
Perhaps you should add the directory containing `pango.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pango' found
configure: error: Package requirements (glib-2.0 >= 2.6.0    atk >= 1.0.1    pango >= 1.8.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

I have successfully installed pango 1.8.2 and atk 1.10.1 with no obvious errors but pkg-config will not find them!
I have even installed pkg-config 0.19 but to no avail.

I must admit that this experience is souring my outlook on Linux.

Can someone offer help - I have trolled the net but find little of help.

Regards to all 
Peter[/QUOTE]


im a noob myself, but i also had problems with pkg-config and that worked:

gedit your /etc/ld.so.conf and add this line:

/usr/local/lib

then run sudo ldconfig

then move all files from /usr/local/lib/pkgconfig to /usr/lib/pkgconfig, and create a link:

ln -s /usr/lib/pkgconfig /usr/local/lib/pkgconfig



however now im stuck when configuring gtk 2.8.9. i get this:

checking Pango flags... -I/usr/local/include/pango-1.0 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/cairo   -L/usr/local/lib -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
configure: error:
*** Can't link to Pango. Pango is required to build
*** GTK+. For more information see [http://www.pango.org](http://www.pango.org)

i have pango 1.10.2, atk 1.10.3, cairo 1.0.2...

my config.log (well... part of it. the one i think is relevant):

configure:31473: checking Pango flags
configure:31479: result: -I/usr/local/include/pango-1.0 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/cairo   -L/usr/local/lib -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
configure:31523: gcc -o conftest -g -O2 -Wall -I/usr/local/include/pango-1.0 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/cairo     -I/usr/X11R6/include  conftest.c -L/usr/local/lib -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    >&5
/usr/local/lib/libpangocairo-1.0.so: undefined reference to `pango_fc_font_create_metrics_for_context'
collect2: ld returned 1 exit status
configure:31529: $? = 1
configure: failed program was:
| /* confdefs.h.  */

anybody get it?

please

---

