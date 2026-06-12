---
title: "GNOME 2.24 Compile fails at Firefox"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by simo on 2008-10-04
So i took some time to copile GNOME 2.24, because i'm on hardy and waiting intrepid.

But, i did install lots of depends, it always fails on firefox

```
../../dist/lib/libgkconcvs_s.a(nsCanvasRenderingContext2D.o): In function `nsCanvasRenderingContext2D::Destroy()':
nsCanvasRenderingContext2D.cpp:(.text+0x20cb): undefined reference to `XFreePixmap'
../../dist/lib/libgkconcvs_s.a(nsCanvasRenderingContext2D.o): In function `nsCanvasRenderingContext2D::SetDimensions(int, int)':
nsCanvasRenderingContext2D.cpp:(.text+0x5dbc): undefined reference to `XRenderFindStandardFormat'
nsCanvasRenderingContext2D.cpp:(.text+0x5ddf): undefined reference to `XListPixmapFormats'
nsCanvasRenderingContext2D.cpp:(.text+0x5e19): undefined reference to `XFree'
nsCanvasRenderingContext2D.cpp:(.text+0x5e63): undefined reference to `XCreatePixmap'
collect2: ld returned 1 exit status
make[7]: *** [libgklayout.so] Error 1
make[7]: Leaving directory `/home/simo/Desktop/garnome-2.24.0/bootstrap/firefox/work/main.d/mozilla/layout/build'
make[6]: *** [libs] Error 2
make[6]: Leaving directory `/home/simo/Desktop/garnome-2.24.0/bootstrap/firefox/work/main.d/mozilla/layout'
make[5]: *** [tier_9] Error 2
make[5]: Leaving directory `/home/simo/Desktop/garnome-2.24.0/bootstrap/firefox/work/main.d/mozilla'
make[4]: *** [default] Error 2
make[4]: Leaving directory `/home/simo/Desktop/garnome-2.24.0/bootstrap/firefox/work/main.d/mozilla'
make[3]: *** [build-work/main.d/mozilla/Makefile] Error 2
make[3]: Leaving directory `/home/simo/Desktop/garnome-2.24.0/bootstrap/firefox'
make[2]: *** [../../bootstrap/firefox/cookies/main.d/install] Error 2
make[2]: Leaving directory `/home/simo/Desktop/garnome-2.24.0/desktop/evolution-data-server'
make[1]: *** [../../desktop/evolution-data-server/cookies/main.d/install] Error 2
make[1]: Leaving directory `/home/simo/Desktop/garnome-2.24.0/desktop/bug-buddy'
make: *** [paranoid-install] Error 2

```

I simply don't know what else to do, so i did some research and found this

[http://www.mail-archive.com/blfs-support@linuxfromscratch.org/msg06736.html]("http://www.mail-archive.com/blfs-support@linuxfromscratch.org/msg06736.html")

After i aplly that it says that "-lx11 no souch file or folder" or something like that

I beg you for help.

Tnx!

---

