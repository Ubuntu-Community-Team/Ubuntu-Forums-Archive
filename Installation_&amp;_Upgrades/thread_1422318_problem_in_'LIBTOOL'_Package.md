---
title: "problem in 'LIBTOOL' Package"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by sanpoonam on 2010-03-05
the following error with 'LIBTOOL' pkg occurs while installing a P2 file for a simulator 

poonam@poonam-desktop:~/bftsim/src/P2$ make
make  all-recursive
make[1]: Entering directory `/home/poonam/bftsim/src/P2'
Making all in eventLoop
make[2]: Entering directory `/home/poonam/bftsim/src/P2/eventLoop'
make[3]: Entering directory `/home/poonam/bftsim/src/P2'
make[3]: Leaving directory `/home/poonam/bftsim/src/P2'
if @LIBTOOL@ --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/include -I../p2core -I../../../EXECS/include -I../../ns/common -I../../ns -I../../tclcl -I../../otcl -I../../include  -DBOOST_DATE_TIME_POSIX_TIME_STD_CONFIG -g -O2 -MT libp2eventLoop_la-loop.lo -MD -MP -MF ".deps/libp2eventLoop_la-loop.Tpo" -c -o libp2eventLoop_la-loop.lo `test -f 'loop.C' || echo './'`loop.C; \
    then mv -f ".deps/libp2eventLoop_la-loop.Tpo" ".deps/libp2eventLoop_la-loop.Plo"; else rm -f ".deps/libp2eventLoop_la-loop.Tpo"; exit 1; fi
/bin/sh: @LIBTOOL@: not found
make[2]: *** [libp2eventLoop_la-loop.lo] Error 1
make[2]: Leaving directory `/home/poonam/bftsim/src/P2/eventLoop'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/poonam/bftsim/src/P2'
make: *** [all] Error 2

---

