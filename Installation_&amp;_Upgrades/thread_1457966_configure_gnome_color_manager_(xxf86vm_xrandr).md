---
title: "configure gnome color manager (xxf86vm xrandr)"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by menelajas on 2010-04-19
ello, I'am new to linux so be gentle to me;)
I was trying to instal gnome color manager but after configuration error I do not know what to do.
Tryed package manager to find xxf86vm and xrandr but no luck


./configure
......
checking for XORG... configure: error: Package requirements (**xxf86vm xrandr**) were not met:

Package xext was not found in the pkg-config search path.
Perhaps you should add the directory containing `xext.pc'
to the PKG_CONFIG_PATH environment variable
Package 'xext', required by 'Xxf86vm', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

------------
Thanks a lot;)

---

### Post by VeeDubb on 2010-04-26
Gnome color manager is available in the repositories.  Just get rid of all the source you downloaded, forget about ./configure, and install it using synaptic.

---

