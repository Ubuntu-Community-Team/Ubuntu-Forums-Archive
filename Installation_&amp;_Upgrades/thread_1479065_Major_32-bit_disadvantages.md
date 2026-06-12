---
title: "Major 32-bit disadvantages?"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by dsimcha on 2010-05-10
I have a laptop with a Celeron 900 CPU and 3 GB of RAM.  It supports 64-bit but not hardware virtualization.  I currently dual-boot Windows 7 64-bit and Ubuntu 10.4 64-bit.  I want to use VMWare Player to allow the same Ubuntu installation to be run on bare metal and in a VM under the Win 7 host (this works well on my desktop, which has an Athlon 64 X2 that does support virtualization).  

The problem is that VMWare Player (and most virtualization software) doesn't support 64-bit guests w/o hardware virtualization.  Given that I only have 3 GB of RAM and will not be increasing this in the foreseeable future, is there any major disadvantage to downgrading to Ubuntu 32-bit so I can run it in a VM w/o hardware virtualization support?  

I understand that 64-bit gives access to more registers, but 32-bit is more cache efficient since pointers are 4 bytes instead of 8.  From looking at benchmarks, it seems 64-bit is faster for some things and 32-bit for others and on average it's pretty much a wash.  Given that 32-bit is firmly in the legacy camp, how much longer will it be well-supported?  Are there any significant features, applications, etc. that are only available on 64-bit besides removing 32-bit address space limitations?  Are there any other major downsides to using 32-bit Ubuntu on 64-bit hardware w/ <= 3 GB of RAM?

Note:  I realize a lot has been written about 32-bit vs. 64-bit before, but most of it is written from the perspective of "why not 64-bit".  I'm interested in more of a "why not 32-bit" perspective.

---

### Post by frantid on 2010-05-10
I'm sure others will pipe in, but I think it's safe to say 32 will be around longer than you will probably want to keep your hardware.  ;)  I think the linux community is not driven by raising profits, thus no need to keep pushing users to the latest and greatest hardware -- it strives to support it, though.  I've an old 386 pentium that still runs a version of linux, I can't even run windows 95 on it.  I don't think you have to worry about losing support for 32 bit.

---

### Post by dalee on 2010-05-10
Hi,

I don't think 32bit is going away soon either. If for no other reason than mobile devices.

But it will go away someday. But not for a few years yet. 

dalee

---

