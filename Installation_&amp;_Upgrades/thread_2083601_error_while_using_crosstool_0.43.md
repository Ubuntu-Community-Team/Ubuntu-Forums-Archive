---
title: "error while using crosstool 0.43"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by tusu on 2012-11-13
Hello while using crosstool0.43 for cross compiling linux for power pc I got this error this seem to me error lies in gcc any idea?

gcc -W -Wall -Wstrict-prototypes -Wmissing-prototypes -g -O2 -o strip-new objcopy.o is-strip.o rename.o rddbg.o debug.o stabs.o ieee.o rdcoff.o wrstabs.o bucomm.o version.o filemode.o  ../bfd/.libs/libbfd.a ../libiberty/libiberty.a
collect2: ld returned 1 exit status
make[3]: *** [strip-new] Error 1
make[3]: Leaving directory `/home/tusu/Downloads/crosstool-0.43/build/powerpc-405-linux-gnu/gcc-3.4.5-glibc-2.3.6/build-binutils/binutils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tusu/Downloads/crosstool-0.43/build/powerpc-405-linux-gnu/gcc-3.4.5-glibc-2.3.6/build-binutils/binutils'
make[1]: *** [all-recursive-am] Error 2
make[1]: Leaving directory `/home/tusu/Downloads/crosstool-0.43/build/powerpc-405-linux-gnu/gcc-3.4.5-glibc-2.3.6/build-binutils/binutils'

---

