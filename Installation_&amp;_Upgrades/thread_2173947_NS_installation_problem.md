---
title: "NS installation problem"
date: 2013-09-12
forum: Installation &amp; Upgrades
---

### Post by shahbaz2 on 2013-09-12
Hello,
I am new to ubuntu and ns tools while installing ns tools i got following error. could any one plz tell me how to resolve this.(i am new to this tools)


cc -c -O2  -pipe  -Wall -fPIC -I/home/shahbaz/Downloads/tk8.5.10/unix/../unix -I/home/shahbaz/Downloads/tk8.5.10/unix/../generic -I/home/shahbaz/Downloads/tk8.5.10/unix/../bitmaps -I/home/shahbaz/Downloads/tcl8.5.10/generic -I/home/shahbaz/Downloads/tcl8.5.10/unix  -DPACKAGE_NAME=\"tk\" -DPACKAGE_TARNAME=\"tk\" -DPACKAGE_VERSION=\"8.5\" -DPACKAGE_STRING=\"tk\ 8.5\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIMITS_H=1 -DSTATIC_BUILD=1 -DMODULE_SCOPE=extern\ __attribute__\(\(__visibility__\(\"hidden\"\)\)\) -DTCL_SHLIB_EXT=\".so\" -DTCL_CFG_OPTIMIZED=1 -DTCL_CFG_DEBUG=1 -D_LARGEFILE64_SOURCE=1 -DTCL_WIDE_INT_IS_LONG=1 -DHAVE_SYS_TIME_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_INTPTR_T=1 -DHAVE_UINTPTR_T=1 -DHAVE_PW_GECOS=1      -DTCL_NO_DEPRECATED    /home/shahbaz/Downloads/tk8.5.10/unix/../generic/tk3d.c
In file included from /home/shahbaz/Downloads/tk8.5.10/unix/../generic/tkInt.h:19:0,
                 from /home/shahbaz/Downloads/tk8.5.10/unix/../generic/tk3d.c:14:
/home/shahbaz/Downloads/tk8.5.10/unix/../generic/tk.h:76:23: fatal error: X11/Xlib.h: No such file or directory
compilation terminated.
make: *** [tk3d.o] Error 1
tk8.5.10 make failed! Exiting ...
For problems with Tcl/Tk see [http://www.scriptics.com](http://www.scriptics.com)

---

