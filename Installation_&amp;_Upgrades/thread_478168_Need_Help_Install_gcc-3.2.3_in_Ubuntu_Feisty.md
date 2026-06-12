---
title: "Need Help Install gcc-3.2.3 in Ubuntu Feisty ?"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by ChenJianYi on 2007-06-19
Hi, I need to install older gcc version for ns-2.26
I have run "./configure" and it was success.

./configure --enable-languages=c,c++ --prefix=/usr/local/gcc-3.2.3/ --exec-prefix=/usr/local/gcc-3.2.3/

But when i run "make", it has an error :

gcc -c -DIN_GCC    -g -O2 -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wtraditional -pedantic -Wno-long-long  -DHAVE_CONFIG_H -DGENERATOR_FILE    -I. -I. -I. -I./. -I./config -I./../include ./read-rtl.c -o read-rtl.o
In file included from ./read-rtl.c:24:
./rtl.h:125: warning: type of bit-field ‘code’ is a GCC extension
./rtl.h:128: warning: type of bit-field ‘mode’ is a GCC extension
./read-rtl.c: In function ‘fatal_with_file_and_line’:
./read-rtl.c:62: warning: traditional C rejects ISO C style function definitions
./read-rtl.c: In function ‘read_rtx’:
./read-rtl.c:662: error: invalid lvalue in increment
make[1]: *** [read-rtl.o] Error 1
make[1]: Leaving directory `/home/dolph1n/Program/gcc-3.2.3/gcc'
make: *** [all-gcc] Error 2

What should I do ?

thank you

---

