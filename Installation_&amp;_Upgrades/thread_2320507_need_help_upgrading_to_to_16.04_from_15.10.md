---
title: "need help upgrading to to 16.04 from 15.10"
date: 2016-04-14
forum: Installation &amp; Upgrades
---

### Post by Miguel_Lopez on 2016-04-14
i have tried everything but it wont find the update to 16.04 beta 2 ... i have a dell inspirion 3000 - 3162 [http://laptoping.com/specs/product/dell-inspiron-11-3000-3162/](http://laptoping.com/specs/product/dell-inspiron-11-3000-3162/)
15.10 works great on it... i have the 64bit version but when i see the iso it says the 64bit 16.04 is only for amd chips

---

### Post by slickymaster on 2016-04-14
*Moved to the ***Installation & Upgrades*** sub-forum*

Xenial release is just a few days away, you'll be able to proceed with the normal upgrade path then. But if you'd like to install and test the latest development version of before it is released, just run at the command line:```
update-manager -c -d
``` This will allow you to upgrade to the current development release.

---

### Post by grahammechanical on 2016-04-14
> but when i see the iso it says the 64bit 16.04 is only for amd chips

No it does not. cdimage.ubuntu.com says regarding 64 bit PC (AMD64) image

> Choose this to take full advantage of computers based on the AMD64 or  EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2).  If  you have a non-64-bit processor made by AMD, or if you need full support  for 32-bit code, use the i386 images instead.

As regards 32 bit PC (i386) desktop image that web site says

> For almost all PCs.  This includes most machines with Intel/AMD/etc type  processors and almost all computers that run Microsoft Windows, as well  as newer Apple Macintosh systems based on Intel processors.  Choose  this if you are at all unsure.

The important thing is whether the CPU is 32 bit or 64 bit. The architecture of 64 bit CPUs whether made by Intel or AMD are backwards compatible with the architecture of 32 bit Intel/AMD line of x86 CPUs.

This means that 32 bit Linux will run on both 32 bit CPUs made by Intel and AMD and also on 64 bit CPUs made by Intel and AMD. But 64 bit Linux will only run on 64 bit CPUs made by Intel or AMD.

So, why is 32 bit Linux called i386 & 64 bit Linux called AMD64? I May be wrong and I may be right but I think that the 80386 was Intel's first 32 bit CPU. AMD brought out their own 32 bit CPU that was compatible with the Intel 80386 (i386) architecture and could run the same 32 bit OS and applications.

AMD extended this technology to produce a 64 bit CPU before Intel did. So, 32 bit Linux references Intel 32 bit CPUs (i386) and 64 bit Linux references AMD 64 bit CPUs (AMD64). But apart from performances differences and as far as computer operating systems go Linux i386 can run on AMD CPUs & Linux AMD64 can run on Intel CPUs.

Regards.

---

