---
title: "kernel-686-smp vs. kernel-686 w/ hyper-threading"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by slightly72 on 2006-03-27
Hi,

Running ubuntu 5.10, and my processor is a Mobile Intel(R) Pentium(R) 4 CPU 2.80GHz (from /proc/cpuinfo). I'm currently running kernel-2.6.12-10-smp, and it seems the whole system is quite slow (slower that what I'd expect from such a processor w/ 512Mb Ram and plenty of cache). The system has a single processor, but the processor comes with hyper-threadings. Now, in /proc/cpuinfo I can see two processors, each of which has the "ht" (hyper-threading) flag on -- which I'm not quite sure how's interpreted by the kernel, it'd seem that the kernel might think that each of the two processors has hyperthreading.

I was wondering what's better to run: the smp kernel, or the plain (single processor) kernel, with hyper-threading enabled? Anyone has some experience with one or the other?

Thank you.

---

### Post by dcstar on 2006-03-29
[QUOTE=slightly72]
.......
I was wondering what's better to run: the smp kernel, or the plain (single processor) kernel, with hyper-threading enabled? Anyone has some experience with one or the other?

Thank you.[/QUOTE]
Install both and choose which you want to load from the boot menu, then you can make up your own mind as to which works better for you.

A CPU is only one component in your computer, unless you run CPU intensive processes simultaneously then you may not see too much of a performance difference on a desktop OS.

---

