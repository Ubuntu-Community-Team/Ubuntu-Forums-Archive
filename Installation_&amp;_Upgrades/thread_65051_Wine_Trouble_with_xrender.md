---
title: "Wine: Trouble with xrender"
date: 2005-09-12
forum: Installation &amp; Upgrades
---

### Post by dumbbeatnix on 2005-09-12
Hello Techies

Maybe you could help me with a small, but large problem.  You see I install wine but get an error message while installing.   It has to do with xrender, and here it is:

gcc -c -I. -I. -I../../include -I../../include -I/usr/X11R6/include -D__WINESRC__   -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2  -o xrender.o xrender.c
xrender.c:1600: error: conflicting types for `X11DRV_XRender_ExtTextOut'
x11drv.h:274: error: previous declaration of `X11DRV_XRender_ExtTextOut'
xrender.c:40: warning: `X11DRV_XRender_Installed' defined but not used
make[2]: *** [xrender.o] Error 1
make[2]: Leaving directory `/home/peter/wine/dlls/x11drv'
make[1]: *** [x11drv] Error 2
make[1]: Leaving directory `/home/peter/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

As you can see from the above, I am installing from tar ball.  The reason being is that it didn't work with deb package and I am not online yet, so I can't use apt-get or winetools.

I may look into previous versions of wine if no-one can help me.  This is from the most recent wine.

Thanks
dumbbeatnix
 ](*,)  ](*,)  ](*,)

---

