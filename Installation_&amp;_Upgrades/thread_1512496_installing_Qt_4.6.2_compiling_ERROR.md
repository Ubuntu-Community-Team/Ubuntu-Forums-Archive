---
title: "installing Qt 4.6.2 compiling ERROR"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by matrronchi on 2010-06-18
Hi there, I tried to install qt and hadn't any problem with ./configure (without any options) but when i compile with 'make' i get a long series of errors: (i quoted only the last ones..)

> ../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:406: error: ‘Ptr_gdk_pixbuf_unref’ does not name a type
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:407: error: ‘Ptr_gdk_drawable_unref’ does not name a type
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:408: error: ‘Ptr_gdk_drawable_get_depth’ does not name a type
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:410: error: ‘Ptr_gdk_x11_window_set_user_time’ does not name a type
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:411: error: ‘Ptr_gdk_x11_drawable_get_xid’ does not name a type
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:412: error: ‘Ptr_gdk_x11_drawable_get_xdisplay’ does not name a type
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:418: error: ‘Ptr_gnome_icon_lookup_sync’ does not name a type
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:419: error: ‘Ptr_gnome_vfs_init’ does not name a type
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:424: error: ‘GtkWidget’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:424: error: template argument 2 is invalid
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:436: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:436: error: ‘GtkWidget’ declared as a ‘virtual’ field
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:436: error: expected ‘;’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:437: error: ‘GtkWidget’ has not been declared
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:438: error: ‘GtkWidget’ has not been declared
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:439: error: ‘GtkWidget’ has not been declared
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:439: error: ‘gpointer’ has not been declared
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:440: error: ‘GtkWidget’ has not been declared
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h: In static member function ‘static bool QGtkStylePrivate::isThemeAvailable()’:
../../include/QtGui/private/../../../src/gui/styles/qgtkstyle_p.h:278: error: ‘gtkStyle’ was not declared in this scope
make[1]: *** [.obj/release-shared/qguiplatformplugin.o] Error 1
make[1]: Leaving directory `/home/matteo/qtsdk-2010.02/qt/src/gui'
make: *** [sub-gui-make_default-ordered] Error 2can anybody help me?
thanks a lot!

Matteo

---

