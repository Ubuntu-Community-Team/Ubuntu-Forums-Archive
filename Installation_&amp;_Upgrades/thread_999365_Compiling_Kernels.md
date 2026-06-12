---
title: "Compiling Kernels"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by kiran88pnjr on 2008-12-01
Hi,

I want to know how to compile a suitable kernel for the following system so that I can improve my performance. 

AMD Athlon x2 4600+ Processor
1GB DDR2 RAM
BoardName :  GeForce 6150SE nForce 430
512 MB Video Memory
Ubuntu Intrepid Ibex 

:):):):):)

---

### Post by lemming465 on 2008-12-02
The easiest way to build a kernel is to install the *build-essential* and *linux-source* metapackages, then switch into /usr/src/linux* and do *make oldconfig* followed by *make all* and *make modules*.  I think; it's been a while since I tried that and the procedure might have mutated.  You'd still have to install it into /boot, make it an initrd, and add it to /boot/grub/menu.lst.

Note that with your CPU you should consider running a 64-bit system; that's probably good for a 15% performance boost over 32-bit due to the increased register set and better virtual memory page table layout.

Also, recompiling the kernel by itself probably won't speed things up much.  But it can be a worthwhile learning experience anyway.

---

