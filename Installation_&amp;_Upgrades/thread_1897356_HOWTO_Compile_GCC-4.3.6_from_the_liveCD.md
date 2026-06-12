---
title: "HOWTO? Compile GCC-4.3.6 from the liveCD?"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by ManDay on 2011-12-19
***Solution: Specifiy LIBRARY_PATH=/usr/lib/x86_64-linux-gnu in the environment, so that the build of GCC finds the x64 libraries in that non-standard place.***

Trying to compile gcc-4.3.6 from upstream source for a system which has been initialized with

```
debootstrap --arch=amd64 oneiric
```

I assume, that makes it multilib. At first I just tried to compile gcc-4.3.6 from my pure amd64 Gentoo host whiich failed, for reasons still not very clear to me. But I assume even if the build had succeeded the resulting executable would not have fully supported the (assumed) multilib ubuntu.

I then tried to make gcc from within the Oneiric LiveCD and this is where I got stuck. At first it fails on configure, which I could resolve by installing

libgmp-dev libmpfr-dev libc6-dev-i386

But then it fails on build because it wants crti.o, to which I can point it by LIBRARY_PATH but then appears to be incompatible arch. I tried then to install libc6-dev-amd64, which appears to be blocked somehow and cannot be resolved.

Ater all, I'm just guessing arround. I don't even know whether libv6-dev-i386 was the right thing to install. Could someone please help?!

---

