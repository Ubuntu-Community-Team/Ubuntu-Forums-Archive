---
title: "error while trying to build gcc"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by varunembar on 2010-04-03
I was trying build gcc 4.1.0 on my 64bit 9.10 ubuntu.
but i got this error


make[4]: *** [32/crtend.o] Error 1
make[4]: *** Waiting for unfinished jobs....
make[4]: *** [32/crtbegin.o] Error 1
In file included from /usr/include/features.h:378,
                 from /usr/include/stdio.h:28,
                 from ../../gcc/tsystem.h:90,
                 from ../../gcc/crtstuff.c:68:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
make[4]: *** [32/crtbeginS.o] Error 1
make[4]: *** [32/crtendS.o] Error 1
make[4]: Leaving directory `/home/varun/Desktop/gcc-4.1.0/objdir/gcc'
make[3]: *** [extra32] Error 2
make[3]: Leaving directory `/home/varun/Desktop/gcc-4.1.0/objdir/gcc'
make[2]: *** [stmp-multilib] Error 2
make[2]: Leaving directory `/home/varun/Desktop/gcc-4.1.0/objdir/gcc'
make[1]: *** [all-gcc] Error 2
make[1]: Leaving directory `/home/varun/Desktop/gcc-4.1.0/objdir'
make: *** [all] Error 2


Can anybody help me?

---

