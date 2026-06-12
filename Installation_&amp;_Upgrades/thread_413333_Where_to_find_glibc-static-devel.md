---
title: "Where to find glibc-static-devel"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by falt004 on 2007-04-19
Hi,

I'm having trouble installing an application which requires glibc-static-devel . I have thebuild-essential as well as libc6-dev and yet for some reason that still seems to be missing.

The program I'm trying to install is Valgrind and their FAQ mentions that I need that:-
[http://valgrind.org/docs/manual/faq.html#faq.glibc_devel](http://valgrind.org/docs/manual/faq.html#faq.glibc_devel)

Cheers,
/Fuad

---

### Post by falt004 on 2007-04-19
Fixed the problem. However, was confronted by another one when trying to install Valgrind on Ubuntu 6.10. Anyway, the solution turned out to be using the gcc option "-fno-stack-protector".

So in case anyone having similar problems find this post, when you configure try:-
./configure CC="gcc -fno-stack-protector"

Cheers,
/Fuad

---

