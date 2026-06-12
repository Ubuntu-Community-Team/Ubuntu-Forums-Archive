---
title: "Monodevelop 1.9.1 source compiling"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by el_rawyy on 2008-08-01
[B][SIZE="3"]Hi everyone

I'm trying to compile monodevelop 1.9.1 source using this command 

====>Command<====
./configure &#8211;prefix=`pkg-config &#8211;variable=prefix mono`
===================================================

but I have an error , I wish to help me to find what is really the problem , and I'll appreciate your help.

====> error <=====

to the PKG_CONFIG_PATH environment variable
No package 'gthread-2.0' found
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 1.3.11) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

=======================================

Thank you all
[/SIZE][/B]

---

### Post by Partyboi2 on 2008-08-01
Try installing the  libglib2.0-dev package

---

### Post by el_rawyy on 2008-08-03
Thank you I'll try it

---

