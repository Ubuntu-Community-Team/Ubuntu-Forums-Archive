---
title: "How to Build and Config X tree"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by jamesfang on 2005-06-24
I have a VIA SP1300 with CN400 motherboard. I need install unichrome driver to get 
hardware accelerate. I download driver from [http://myth.ivor.org/unichrome/](http://myth.ivor.org/unichrome/).  and try install acoording to following menual:
=============================================
1. Build drm (for 2.6 kernel)
(Clearly here replace <linux-2.6.11> with your source location.)

    cd drm/linux-core
    make LINUXDIR=/usr/src/<linux-2.6.11> DRM_MODULES=via
    cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
    depmod -ae

2. Build libxvmc
(If building inside an X tree comment out the OUTOFTREE directive in the Imakefile)

    cd libxvmc
    xmkmf /usr/src/xc
    make
    make install

3. Build driver

    cd unichrome
    xmkmf /usr/src/xc
    make
    make install
===============================================

when I do the second step(2. Build libxvmc ). I get many error. I need config X tree. how should I config? I am a newbie in linux. the following is error prompt :

root@MediaCenter:/home/mythtv/unichrome-20050622/libxvmc # xmkmf /usr/src/xorg-6.8.2/xc

mv -f Makefile Makefile.bak
imake -I/usr/src/xorg-6.8.2/xc/config/cf -DTOPDIR=/usr/src/xorg-6.8.2/xc -DCURDIR=.
In file included from /usr/src/xorg-6.8.2/xc/config/cf/Imake.tmpl:46,
                 from Imakefile.c:40:
/usr/src/xorg-6.8.2/xc/config/cf/site.def:44: host.def: No such file or directory
In file included from /usr/src/xorg-6.8.2/xc/config/cf/linux.cf:1029,
                 from /usr/src/xorg-6.8.2/xc/config/cf/Imake.tmpl:105,
                 from Imakefile.c:40:
/usr/src/xorg-6.8.2/xc/config/cf/xorg.cf:13: date.def: No such file or directoryIn file included from /usr/src/xorg-6.8.2/xc/config/cf/Imake.tmpl:111,
                 from Imakefile.c:40:
/usr/src/xorg-6.8.2/xc/config/cf/site.def:146: host.def: No such file or directory
imake: Exit code 1.
  Stop.
root@MediaCenter:/home/mythtv/unichrome-20050622/libxvmc #

---

