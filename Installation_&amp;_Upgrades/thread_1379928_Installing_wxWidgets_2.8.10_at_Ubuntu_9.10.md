---
title: "Installing wxWidgets 2.8.10 at Ubuntu 9.10"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by jecdiniz on 2010-01-13
I tryed to install the wxWidgets at Ubuntu 9.10 and I use the following command:

I use the following command:
../configure --prefix=$(pwd) --enable-shared --enable-monolithic --with-gtk=2 --with-libpng=builtin --with-zlib=builtin --with-expat=builtin --with-libtiff=builtin --with-regex=builtin --with-libjpeg=builtin --enable-unicode --enable-debug

After I use the command "make" I got the following errors:

/home/jecdiniz/buildgtk/wxGTK-2.8.10/build/bk-deps g++ -c -o coredll_gtk_gsockgtk.o -I./.pch/wxprec_coredll -D__WXGTK__     -I../src/tiff     -I../src/regex  -DWXUSINGDLL -DWXMAKINGDLL_CORE -DwxUSE_BASE=0 -fPIC -DPIC -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXDEBUG__ -I/home/jecdiniz/buildgtk/wxGTK-2.8.10/build/lib/wx/include/gtk2-unicode-debug-2.8 -I../include -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DWX_PRECOMP -pthread -Wall -Wundef -Wno-ctor-dtor-privacy -g -O0 ../src/gtk/gsockgtk.cpp
In file included from ../src/gtk/gsockgtk.cpp:21:
../include/wx/gsocket.h:40: error: using typedef-name ‘GSocket’ after ‘class’
/usr/include/glib-2.0/gio/giotypes.h:120: error: ‘GSocket’ has a previous declaration here
In file included from ../include/wx/gsocket.h:179,
                 from ../src/gtk/gsockgtk.cpp:21:
../include/wx/unix/gsockunx.h:40: error: using typedef-name ‘GSocket’ after ‘class’
/usr/include/glib-2.0/gio/giotypes.h:120: error: ‘GSocket’ has a previous declaration here
../src/gtk/gsockgtk.cpp: In function ‘void _GSocket_GDK_Input(void*, gint, GdkInputCondition)’:
../src/gtk/gsockgtk.cpp:34: error: ‘struct _GSocket’ has no member named ‘Detected_Read’
../src/gtk/gsockgtk.cpp:36: error: ‘struct _GSocket’ has no member named ‘Detected_Write’
../src/gtk/gsockgtk.cpp: In member function ‘virtual bool GSocketGUIFunctionsTableConcrete::Init_Socket(GSocket*)’:
../src/gtk/gsockgtk.cpp:56: error: ‘struct _GSocket’ has no member named ‘m_gui_dependent’
../src/gtk/gsockgtk.cpp:57: error: ‘struct _GSocket’ has no member named ‘m_gui_dependent’
../src/gtk/gsockgtk.cpp: In member function ‘virtual void GSocketGUIFunctionsTableConcrete::Destroy_Socket(GSocket*)’:
../src/gtk/gsockgtk.cpp:67: error: ‘struct _GSocket’ has no member named ‘m_gui_dependent’
../src/gtk/gsockgtk.cpp: In member function ‘virtual void GSocketGUIFunctionsTableConcrete::Install_Callback(GSocket*, GSocketEvent)’:
../src/gtk/gsockgtk.cpp:72: error: ‘struct _GSocket’ has no member named ‘m_gui_dependent’
../src/gtk/gsockgtk.cpp:75: error: ‘struct _GSocket’ has no member named ‘m_fd’
../src/gtk/gsockgtk.cpp:83: error: ‘struct _GSocket’ has no member named ‘m_server’
../src/gtk/gsockgtk.cpp:90: error: ‘struct _GSocket’ has no member named ‘m_fd’
../src/gtk/gsockgtk.cpp: In member function ‘virtual void GSocketGUIFunctionsTableConcrete::Uninstall_Callback(GSocket*, GSocketEvent)’:
../src/gtk/gsockgtk.cpp:98: error: ‘struct _GSocket’ has no member named ‘m_gui_dependent’
../src/gtk/gsockgtk.cpp:108: error: ‘struct _GSocket’ has no member named ‘m_server’
make: ** [coredll_gtk_gsockgtk.o] Erro 1
jecdiniz@jecdiniz-desktop:~/buildgtk/wxGTK-2.8.10/build$ 

And I would like to know what is wrong.

TIA
Eduardo

---

