---
title: "compile error"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by sohaibma on 2007-05-05
i am compiling a program. when i enter the ./configure command. it gives me the following error.

```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.2.0 gdk-2.0 gconf-2.0 gdk-pixbuf-xlib-2.0) were not met:

No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

when i checked in synaptic, it showed that i have already installed the gconf-2.0 package. how do i fix this error?

---

### Post by Theimon on 2007-05-05
Maybe it needs the dev package for gconf-2.0, I think that would be libgconf-dev, so:```
sudo aptitude install libgconf-dev
```

---

### Post by sohaibma on 2007-05-05
no, that did not do.
it is showing the same error even after the installation of the package.

---

### Post by Theimon on 2007-05-06
I don't know what program you're compiling but have you checked that all these packages are installed?
gtk+-2.0 >= 2.2.0 
gdk-2.0 
gconf-2.0 
gdk-pixbuf-xlib-2.0

---

