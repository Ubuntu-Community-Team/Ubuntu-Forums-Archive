---
title: "[SOLVED] Install Davids Batch Processor for GIMP"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by SneakPeak on 2008-01-12
Hi

I am trying to install David's Batch Processor (DBP) for Gimp.  One had to compile it to install.  Something I know dangerously little about.  I have tried make and make install and I get the same error message which I have pasted in below.  I had DBP working in 6.06 but I can't get it up and running in 7.10 and I really need it.  Any help appreciated:

adrian@adrian-desktop:~/Downloads/Gimp_Plugins/DavidsBatchProcessor/dbp-1.1.7$ make
g++ -o dbp -Wall -O2 -I. *.cc -I/usr/include/gimp-2.0 -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12  -lgimpui-2.0 -lgimpwidgets-2.0 -lgimpmodule-2.0 -lgimp-2.0 -lgimpmath-2.0 -lgimpconfig-2.0 -lgimpcolor-2.0 -lgimpbase-2.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -DGTK_DISABLE_DEPRECATED
gui.cc: In member function ‘virtual GtkWidget* Dbp::RenameGui::build()’:
gui.cc:875: error: ‘gtk_file_selection_new’ was not declared in this scope
gui.cc:878: error: ‘GtkFileSelection’ was not declared in this scope
gui.cc:878: error: ‘fs’ was not declared in this scope
gui.cc:878: error: ‘GTK_FILE_SELECTION’ was not declared in this scope
gui.cc:886: error: ‘gtk_file_selection_hide_fileop_buttons’ was not declared in this scope
gui.cc: In member function ‘void Dbp::RenameGui::okDirSelector()’:
gui.cc:997: error: ‘GTK_FILE_SELECTION’ was not declared in this scope
gui.cc:997: error: ‘gtk_file_selection_get_filename’ was not declared in this scope
make: *** [dbp] Error 1

---

### Post by SneakPeak on 2008-01-12
Hi All,

I solved the problem thanks to help from the author of the plug-in.  All you need to do is comment out the following line in the Makefile:

NODEPS = -DGTK_DISABLE_DEPRECATED

To comment it out just put a # symbol at the start of the line.

Cheers

Sneaks

---

