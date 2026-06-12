---
title: "Attempting to install Firefox-1.0.7"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by zarathustra on 2005-09-21
When I try to run the installer I get this error:

> nick@kitsune:~/downloads/firefox-installer$ ./firefox-installer

(firefox-installer-bin:20486): Gdk-WARNING **: locale not supported by Xlib

(firefox-installer-bin:20486): Gdk-WARNING **: can not set locale modifiers

(firefox-installer-bin:20486): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-installer-bin:20486): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-installer-bin:20486): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:20486): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:20486): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:20486): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:20486): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:20486): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:20486): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:20486): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:20486): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(firefox-installer-bin:20486): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:20486): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:20486): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (firefox-installer-bin:20486): CRITICAL **: file pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
./firefox-installer: line 56: 20486 Aborted                 ./${BINNAME}-bin $@

I have no idea what to do, I have all dependencies installed. Anyone know what is wrong?

---

### Post by John.Michael.Kane on 2005-09-21
You can save the file to your desktop. open terminal type cd Desktop then  tar -xzvf firefox-1.0.7.installer.tar.gz 


Take the folder thats made and copy the files to /usr/lib/mozilla-firefox  using sudo nautilus type that in the run apps section..


hope that helps

---

### Post by zarathustra on 2005-09-21
Tried that with the installer and the binaries, nothing works!

---

