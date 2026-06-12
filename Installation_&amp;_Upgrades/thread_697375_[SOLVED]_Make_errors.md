---
title: "[SOLVED] Make errors"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by serpantman on 2008-02-15
I am trying to install authforce from source. Configure file ran fine. But make came back with an error. I've included the output of make and make check. If there is anyway to look into these types of errors on my own i would like to know. I had trouble finding anything.

make output :: 

make  all-recursive
make[1]: Entering directory `/home/tourva/HTTPBruteForcer/authforce-0.9.9'
Making all in data
make[2]: Entering directory `/home/tourva/HTTPBruteForcer/authforce-0.9.9/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tourva/HTTPBruteForcer/authforce-0.9.9/data'
Making all in src
make[2]: Entering directory `/home/tourva/HTTPBruteForcer/authforce-0.9.9/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../intl -DLOCALEDIR=\"/usr/local/share/locale\"    -g -O2 -MT config.o -MD -MP -MF ".deps/config.Tpo" -c -o config.o config.c; \
        then mv -f ".deps/config.Tpo" ".deps/config.Po"; else rm -f ".deps/config.Tpo"; exit 1; fi
config.c:8:28: error: readline/tilde.h: No such file or directory
config.c: In function ‘parse_config’:
config.c:39: warning: assignment makes pointer from integer without a cast
make[2]: *** [config.o] Error 1
make[2]: Leaving directory `/home/tourva/HTTPBruteForcer/authforce-0.9.9/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tourva/HTTPBruteForcer/authforce-0.9.9'
make: *** [all] Error 2

make check output ::

Making check in data
make[1]: Entering directory `/home/tourva/HTTPBruteForcer/authforce-0.9.9/data'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/tourva/HTTPBruteForcer/authforce-0.9.9/data'
Making check in src
make[1]: Entering directory `/home/tourva/HTTPBruteForcer/authforce-0.9.9/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../intl -DLOCALEDIR=\"/usr/local/share/locale\"    -g -O2 -MT config.o -MD -MP -MF ".deps/config.Tpo" -c -o config.o config.c; \
        then mv -f ".deps/config.Tpo" ".deps/config.Po"; else rm -f ".deps/config.Tpo"; exit 1; fi
config.c:8:28: error: readline/tilde.h: No such file or directory
config.c: In function ‘parse_config’:
config.c:39: warning: assignment makes pointer from integer without a cast
make[1]: *** [config.o] Error 1
make[1]: Leaving directory `/home/tourva/HTTPBruteForcer/authforce-0.9.9/src'
make: *** [check-recursive] Error 1

Any help at understanding this would be appreciated, even though the "makes pointer from integer without a cast", sounds like im screwed. Any helpful thoughts or links would  be greatly appreciated.

---

### Post by lloyd_b on 2008-02-15
It looks like you're missing the development headers for the "readline" library.  Try installing them ("sudo apt-get install libreadline5-dev" (or lib64readline-dev, for 64 bit systems) in a terminal window, or via the package manager of your choice) and see if you get a clean compile.

Assuming this fixes it, I'd suggest letting the developers know about the issue - if these headers are required, then "configure" should ideally detect whether or not they are there.

Lloyd B.

---

### Post by serpantman on 2008-02-15
It worked even tho there was no lib64readline-dev that could be found by my package manager, i downloaded the whole libreadline5 package for 64-bit, thanks you!!

---

