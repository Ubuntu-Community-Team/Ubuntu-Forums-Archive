---
title: "ubuntu11.10 upgrade and glibc"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by nozarm on 2011-11-18
Hello,

I am having linker issues after upgrading from 11.04 to 11.10:

gcc version 3.4.6 (Ubuntu 3.4.6-6ubuntu5)
 ld --eh-frame-hdr -m elf_i386 -dynamic-linker /lib/ld-linux.so.2 -o Elec_dUCx_50MeV crt1.o crti.o crtbegin.o -L/opt/src/fluka/2011.2.6 -L/usr/lib/gcc/i486-linux-gnu/3.4.6 -L/usr/lib/gcc/i486-linux-gnu/3.4.6 -L/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib -L/usr/lib/gcc/i486-linux-gnu/3.4.6/../../.. -L/lib/../lib -L/usr/lib/../lib -Map Elec_dUCx_50MeV.map fluka.o -lflukahp -lfrtbegin -lg2c -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc crtend.o crtn.o
ld: cannot find crt1.o: No such file or directory
ld: cannot find crti.o: No such file or directory
ld: cannot find crtbegin.o: No such file or directory
ld: cannot find -lgcc_s
ld: cannot find -lgcc


========================================================
> gcc --version
gcc (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1

> locate gcc_s
/lib/i386-linux-gnu/libgcc_s.so.1
/usr/lib/gcc_old/i486-linux-gnu.old/3.4.6/libgcc_s.so
/usr/lib/gcc_old/i486-linux-gnu.old/3.4.6/libgcc_s_64.so
/usr/lib/gcc_old/i486-linux-gnu.old/3.4.6/64/libgcc_s.so
/usr/lib/gcc_old/i486-linux-gnu.old/3.4.6/64/libgcc_s_64.so
/usr/lib/gcc_old/i686-linux-gnu.old/4.6/libgcc_s.so
/usr/lib/ure/lib/libgcc_s.so.1

> locate crti.o
/usr/lib/debug/usr/lib/i386-linux-gnu/crti.o
/usr/lib/debug/usr/lib64/crti.o
/usr/lib/i386-linux-gnu/crti.o


> more /etc/ld.so.conf.d/libc.conf
# libc default configuration
#/usr/local/lib
/usr/lib/i386-linux-gnu

---

