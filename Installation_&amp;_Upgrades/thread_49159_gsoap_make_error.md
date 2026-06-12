---
title: "gsoap make error"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by MBMESSAOUD on 2005-07-15
Hi 

Does anyone know about this error when making gsoap

gcc -DHAVE_CONFIG_H -I. -I. -I../..    -DWITH_YACC -DWITH_FLEX  -DLINUX -g -O2 -c -o soapcpp2-soapcpp2.o `test -f 'soapcpp2.c' || echo './'`soapcpp2.c
gcc  -g -O2   -o soapcpp2  soapcpp2-soapcpp2_yacc.o soapcpp2-soapcpp2_lex.o soapcpp2-symbol2.o soapcpp2-error2.o soapcpp2-init2.o soapcpp2-soapcpp2.o -ly -lfl
**/usr/bin/ld: cannot find -ly**
collect2: ld returned 1 exit status
make[4]: *** [soapcpp2] Error 1

---

