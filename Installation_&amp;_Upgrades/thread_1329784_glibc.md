---
title: "glibc"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by PaulCi on 2009-11-17
Hello:

I am trying to compile an old graphics package called grafic.  I have it working on a Mac but I want to also use it on ubuntu.

When I make it I get 

cizmas@lbu:~/codes/a/util/grafic/graficV3/util$ make -f Makefile_ubuntu_gfortran 
\
         gfortran -o /home/cizmas/codes/a/util/grafic/graficV3/demo/grtest\
                       /home/cizmas/codes/a/util/grafic/graficV3/src/Grtest.o\
                       /home/cizmas/codes/a/util/grafic/graficV3/Xathena.o /usr/lib/libX11.a /usr/lib/libxcb.a /usr/lib/libxcb-xlib.a /usr/lib/libdl.a 
/usr/lib/libX11.a(CrGlCur.o): In function `open_library':
(.text+0x25): warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/libxcb.a(xcb_auth.o): In function `_xcb_get_auth_info':
(.text+0x380): undefined reference to `XauGetBestAuthByAddr'
/usr/lib/libxcb.a(xcb_auth.o): In function `_xcb_get_auth_info':
(.text+0x414): undefined reference to `XauDisposeAuth'
/usr/lib/libxcb.a(xcb_auth.o): In function `_xcb_get_auth_info':
(.text+0x4f2): undefined reference to `XdmcpWrap'
/usr/lib/libdl.a(dlopen.o): In function `dlopen':
(.text+0x5): undefined reference to `__dlopen'
/usr/lib/libdl.a(dlsym.o): In function `dlsym':
(.text+0x5): undefined reference to `__dlsym'
collect2: ld returned 1 exit status
make: *** [/home/cizmas/codes/a/util/grafic/graficV3/demo/grtest] Error 1
cizmas@lbu:~/codes/a/util/grafic/graficV3/util$ 

It looks that I have a problem with the glibc library.  Here are my questions:

1. Is my assumption correct?
2. If yes, what package is glibc in (and how can I find this out)?

Thank you,

Paul

---

