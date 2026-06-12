---
title: "Compiler error: gobject is required to build pygtk"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by napy84 on 2007-09-22
I've this error during the compiling of the pygtk package:

```
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.8.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.14.0, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: gobject is required to build pygtk?
```
I've set the variable environment PKG_CONFIG_PATH on the .bashrc file in my home directory, as:
```
PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig
```
but I obtain the same error.:confused::confused:
Can someone help me?
Thanks (and excuse me for my english :popcorn:)

---

