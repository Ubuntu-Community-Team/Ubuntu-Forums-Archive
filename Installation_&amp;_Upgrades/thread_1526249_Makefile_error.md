---
title: "Makefile error?"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by pitorito on 2010-07-07
Hi guys
I was trying to install my Genis Webcam, so I downloaded the drivers from [http://mxhaard.free.fr/](http://mxhaard.free.fr/).
I entered with root user and I did all the steps. When I have to execute the MAKE file appears this error:


Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/local/src/spca5xx-v4l1goodbye CC=cc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.32-22-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/usr/local/src/spca5xx-v4l1goodbye/Makefile". Fix it to use EXTRA_CFLAGS.  Alto.
make[1]: *** [_module_/usr/local/src/spca5xx-v4l1goodbye] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [default] Error 2

:(

I don't know what to do.

---

