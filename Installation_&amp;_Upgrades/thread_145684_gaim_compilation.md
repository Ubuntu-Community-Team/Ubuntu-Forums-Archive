---
title: "gaim compilation"
date: 2006-03-16
forum: Installation &amp; Upgrades
---

### Post by yohan on 2006-03-16
I tried downloading the game 2 beta 2 source for compilation but ive had some trouble.

when doing a ./configure i get the following error:
checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.8.6, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).

First I got an error saying I had glib 2.8.3 which wasnt enough...then i downloaded the newest glib and compiled that, and i got this error. I also cant compile the latest gtk source because of the same dependency error. Why is this? What can I do? Can I uninstall glib 2.8.3 somehow? I tried downloading the source of 2.8.3 and then doing a make uninstall...but after i tried that i got the same error.

Any help appreciated!

---

### Post by Zelut on 2006-03-16
I put together a wiki that I used to compile gaim beta 1 & its worked fine.  Maybe give that a try & see if it works for gaim beta 2 as well?

[https://wiki.ubuntu.com/CompileGaim](https://wiki.ubuntu.com/CompileGaim)

---

