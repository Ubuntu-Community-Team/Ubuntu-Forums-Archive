---
title: "gnome-maps not working after upgrading to 20.04"
date: 2020-05-10
forum: Installation &amp; Upgrades
---

### Post by orj-gmail on 2020-05-10
Gnome-maps not working after upgrading to 20.04.
After upgrade all worked fine, the only thing that won't work was gnome-maps.
I deleted and reinstalled it (via snapstore and synaptic) but nothing changed.
When I try to start it via terminal, I get the following output:

chris@yoyo:~$ gnome-maps

(org.gnome.Maps:13930): Gtk-WARNING **: 21:37:09.398: Theme parsing error: gtk.css:661:53: Expected ',' in color definition

(org.gnome.Maps:13930): Gtk-WARNING **: 21:37:09.398: Theme parsing error: gtk.css:675:58: Expected ',' in color definition

(org.gnome.Maps:13930): Gtk-WARNING **: 21:37:09.399: Theme parsing error: gtk.css:825:58: Expected ',' in color definition

(org.gnome.Maps:13930): Gtk-WARNING **: 21:37:09.399: Theme parsing error: gtk.css:1046:58: Expected ',' in color definition

(org.gnome.Maps:13930): Gtk-WARNING **: 21:37:09.420: Theme parsing error: gtk.css:10358:58: Expected ',' in color definition

(org.gnome.Maps:13930): Gtk-WARNING **: 21:37:09.420: Theme parsing error: gtk.css:10367:58: Expected ',' in color definition

(org.gnome.Maps:13930): Gtk-WARNING **: 21:37:09.420: Theme parsing error: gtk.css:10380:58: Expected ',' in color definition

(org.gnome.Maps:13930): Gtk-WARNING **: 21:37:09.420: Theme parsing error: gtk.css:10391:58: Expected ',' in color definition
Gdk-Message: 21:37:10.410: Error 71 (Protokollfehler) dispatching to Wayland display.

I have no idea what to do, to get gnome-maps running.

---

