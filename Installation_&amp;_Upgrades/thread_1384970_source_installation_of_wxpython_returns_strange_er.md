---
title: "source installation of wxpython returns strange error"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by srinivas2828 on 2010-01-19
I am trying to install wxpython from the source tar ball and which gave me error when i ran command ./configure and here is the error output
```

checking for GTK+ version... 
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.


```

and i ran a couple of commands from the error to check the paths
```

                            
root@miriyala-laptop:/home/miriyala/Downloads/wxPython-src-2.8.10.1# pkg-config gtk+-2.0 --libs
-lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0

```
any idea what is going on

---

### Post by Leppie on 2010-01-19
maybe a silly question, but do you have the package libgtk2.0-dev installed?

---

### Post by srinivas2828 on 2010-01-28
it looks like silly problem but i have installed everything that all the people have suggested but no use and at last I compiled from source and the its worked fine for me but I  am not able to solve the original problem

---

