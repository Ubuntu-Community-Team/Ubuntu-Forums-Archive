---
title: "Gaim Video And Voice (gaim-vv) Support problem"
date: 2005-06-02
forum: Installation &amp; Upgrades
---

### Post by BabyUbuntu on 2005-06-02
i tried to install gaim-vv coz i wanna using my logitech webcam and using voice too... but i've problem when i install it ...

root@ubuntu:~/babyubuntu/gaim-vv-1.2.0 #./configure
.
.
.
.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.0.0, but GLIB (2.6.3)
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

**than i installed GLib 2.0 is required to  build Gaim .**

[B]root@ubuntu:/ # whereis glib-2.0
glib-2: /usr/lib/glib-2.0 /usr/local/lib/glib-2.0 /usr/include/glib-2.0 /usr/share/glib-2.0[/B]

root@ubuntu:/ # dpkg -l |grep libglib2
ii  libglib2.0-0   2.6.3-1        The GLib library of C routines
ii  libglib2.0-dat 2.6.3-1        Common files for GLib library
ii  libglib2.0-dev 2.6.3-1        Development files for the GLib library

i tried again to install gaim-vv.. but i still got same comment..

root@ubuntu:~/babyubuntu/gaim-vv-1.2.0 #./configure
.
.
.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.0.0, but GLIB (2.6.3)
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

pls tell me what i have to do.. step by step.. with my problem.. thx

---

