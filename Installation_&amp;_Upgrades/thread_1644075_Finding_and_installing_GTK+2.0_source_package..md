---
title: "Finding and installing GTK+2.0 source package."
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by thelazydeveloper on 2010-12-12
I'm attempting to debug an xchat crash, it spits the following at me when I break on gdk_x_error: 

/build/buildd/gtk+2.0-2.22.0/gdk/x11/gdkmain-x11.c: No such file or directory.

when I try to download the gtk+2.0 source package via:

sudo apt-get source gtk+2.0

it tells me no source package was found. I saw this package: [http://packages.ubuntu.com/source/maverick/gtk+2.0](http://packages.ubuntu.com/source/maverick/gtk+2.0) thought I could just apt-get it but I'm unsure why it fails and where to go from here. 

Is this the right source package that contains gdkmain-x11.c? 
If it isn't, where might I find the correct package as I've installed a ton of gnome, glib, gtk packages along with their associated -dev/-dbg packages.

---

