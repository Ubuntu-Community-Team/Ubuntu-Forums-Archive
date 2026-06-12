---
title: "Problems Building Anjuta from SVN"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by cppide on 2008-10-19
I am trying to build anjuta revision 4357 from svn. I have all the dependencies and the configuration passes. Trying to build anjuts, however, is where I find the problem.
The building process fails with:
```

gcc -DHAVE_CONFIG_H -I. -I../.. -DORBIT2=1 -pthread -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/gnome-vfs-module-2.0 -I/usr/include/libgnomeprint-2.2 -I/usr/include/libgnomeprintui-2.2 -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I../.. -DPACKAGE_PIXMAPS_DIR=\"/usr/share/pixmaps/anjuta\" -DPACKAGE_LIB_DIR=\"/usr/lib/anjuta\" -DPACKAGE_DATA_DIR=\"/usr/share/anjuta\" -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare -I/usr/local/include/libgdl-1.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/include/libglade-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/graphviz -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare -DDEBUG -g -O2 -MT class-inherit.lo -MD -MP -MF .deps/class-inherit.Tpo -c class-inherit.c  -fPIC -DPIC -o .libs/class-inherit.o
class-inherit.c: In function ‘cls_inherit_draw_graph’:
class-inherit.c:820: warning: implicit declaration of function ‘ND_coord_i’
class-inherit.c:820: warning: nested extern declaration of ‘ND_coord_i’
class-inherit.c:820: error: incompatible types in assignment
make[3]: *** [class-inherit.lo] Error 1
make[3]: Leaving directory `/home/adam/development/anjuta/anjuta/plugins/class-inheritance'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/adam/development/anjuta/anjuta/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/adam/development/anjuta/anjuta'
make: *** [all] Error 2


```

This problem has been troubling me for quite a while and I would grateful if someone could help me out with this.

Thanks in advance.

---

### Post by cppide on 2008-10-27
Please, I would really like some help with this issue.

---

