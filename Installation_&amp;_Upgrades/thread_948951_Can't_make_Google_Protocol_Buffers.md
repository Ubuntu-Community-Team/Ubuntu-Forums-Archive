---
title: "Can't make Google Protocol Buffers"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by BobtheBlueBerry on 2008-10-15
Hi.
I'm trying to install Google Protocol Buffers on Ubuntu.
[FONT="System"]configure[/FONT] Works, but [FONT="System"]make[/FONT] fails:
> bob@bob:~/Downloads/protobuf-2.0.2$ make
make  all-recursive
make[1]: Entering directory `/home/bob/Downloads/protobuf-2.0.2'
Making all in src
make[2]: Entering directory `/home/bob/Downloads/protobuf-2.0.2/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -pthread -Wall -Wwrite-strings -Woverloaded-virtual -Wno-sign-compare -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o `test -f 'google/protobuf/compiler/main.cc' || echo './'`google/protobuf/compiler/main.cc; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
if /bin/bash ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I..    -pthread -Wall -Wwrite-strings -Woverloaded-virtual -Wno-sign-compare -g -O2 -MT common.lo -MD -MP -MF ".deps/common.Tpo" -c -o common.lo `test -f 'google/protobuf/stubs/common.cc' || echo './'`google/protobuf/stubs/common.cc; \
	then mv -f ".deps/common.Tpo" ".deps/common.Plo"; else rm -f ".deps/common.Tpo"; exit 1; fi
../libtool: **xmalloc: ../bash/make_cmd.c:99: cannot allocate 38116325 bytes (0 bytes allocated)**
make[2]: *** [common.lo] Error 1
make[2]: Leaving directory `/home/bob/Downloads/protobuf-2.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bob/Downloads/protobuf-2.0.2'
make: *** [all] Error 2

See in the bold? It pauses for a minute before it prints that and then fails.

Thanks,

Bob

---

