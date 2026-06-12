---
title: "sane backend install error"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by itachisxeyes on 2010-01-08
ok as the name states i'm installing sane backend,
i made it past ./configure just fine but when i run the make command i get this:
```
alex@Eliza:~/Downloads/sane$ make
Making all in include
make[1]: Entering directory `/home/alex/Downloads/sane/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/alex/Downloads/sane/include'
Making all in lib
make[1]: Entering directory `/home/alex/Downloads/sane/lib'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/usr/local/etc/sane.d       -DPATH_SANE_DATA_DIR=/usr/local/share   -DPATH_SANE_LOCK_DIR=/usr/local/var/lock/sane       -DV_MAJOR=1 -DV_MINOR=0  -g -O2 -W -Wall -MT alloca.lo -MD -MP -MF .deps/alloca.Tpo -c -o alloca.lo alloca.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../include/sane -I/usr/local/include -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/usr/local/etc/sane.d -DPATH_SANE_DATA_DIR=/usr/local/share -DPATH_SANE_LOCK_DIR=/usr/local/var/lock/sane -DV_MAJOR=1 -DV_MINOR=0 -g -O2 -W -Wall -MT alloca.lo -MD -MP -MF .deps/alloca.Tpo -c alloca.c  -fPIC -DPIC -o .libs/alloca.o
alloca.c:26: fatal error: opening dependency file .deps/alloca.Tpo: Permission denied
compilation terminated.
make[1]: *** [alloca.lo] Error 1
make[1]: Leaving directory `/home/alex/Downloads/sane/lib'
make: *** [all-recursive] Error 1
alex@Eliza:~/Downloads/sane$ 
```

---

