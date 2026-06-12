---
title: "Error on installing Wepattack"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by pattelin on 2010-10-09
Hi,

I am trying to install the latest version of wepattack on Ubuntu 10.04 (64 bits) and I am getting the following error:

root@laptop2:/home/jay1/WepAttack-0.1.3/src# make
gcc -fno-for-scope -c -D__LINUX_WLAN__ -D__I386__ -o wepfilter.o wepfilter.c
cc1: warning: command line option "-fno-for-scope" is valid for C++/ObjC++ but not for C
wepfilter.c: In function ‘my_callback’:
wepfilter.c:131: error: assignment of read-only location ‘*pkthdr’
wepfilter.c:132: error: assignment of read-only location ‘*pkthdr’
make: *** [wepfilter.o] Error 1

Any ideas about why?

Thanx

:P

---

