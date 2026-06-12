---
title: "error while upgrading alsa 1.0.9"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by badnaam on 2011-01-26
Here is my ubuntu version


Linux  2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

I downloaded the driver into /usr/src and tried to do a configure and then a make. I get the following error.

I am following instructions from this page.

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9/acore'
copying file alsa-kernel/core/sound.c
patching file sound.c
Hunk #1 succeeded at 64 (offset -1 lines).
Hunk #2 succeeded at 164 with fuzz 2 (offset -1 lines).
Hunk #3 succeeded at 365 (offset -5 lines).
Hunk #4 succeeded at 380 (offset -7 lines).
Hunk #5 succeeded at 500 (offset -3 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #1 succeeded at 1274 (offset 7 lines).
Hunk #2 succeeded at 1357 (offset 7 lines).
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #1 succeeded at 993 (offset -2 lines).
Hunk #2 succeeded at 1842 (offset 51 lines).
Hunk #3 succeeded at 1896 (offset 51 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
gcc -D__KERNEL__ -DMODULE=1 -I/usr/src/alsa/alsa-driver-1.0.9/include  -I/lib/modules/2.6.35-24-generic/build/include -O2  -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include   -DEXPORT_SYMTAB -c memalloc.c
In file included from memalloc.c:1:
memalloc.inc:1: fatal error: linux/config.h: No such file or directory
compilation terminated.
make[1]: *** [memalloc.o] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9/acore'
make: *** [compile] Error 1

---

