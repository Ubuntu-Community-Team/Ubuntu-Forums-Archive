---
title: "Worth Changing the Kernel?"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by Coolit on 2006-02-28
I have an Ubuntu 5.10 P4 64bit system with the stock "generic" 2.6.11.2 64 bit kernel that is installed by default. I've noticed that there is a 2.6.11.9 Intel EM64T compiled kernel available on apt.

I was wondering as I have a P4 with EM64T extensions whether it was worth changing to this kernel and which benefits I could expect to get, performance wise etc...? Are there any draw backs? (except having to re-compile my Nvidia drivers again).

Thanks for any replies :)

oh...and what is the difference with the SMP compiles, HT ready mibi?

---

### Post by jpkotta on 2006-02-28
It can't hurt to try.  One of the strengths of Linux is that you can configure the kernel (or someone else can and you can use theirs).  Plus it's easy to switch back if it doesn't work.  

SMP kernels are needed for HyperThreading, as far as I know.

---

### Post by Coolit on 2006-02-28
I gave it a go but the load fails during the boot process with...

**/bin/sh: can't access tty; job control turned off**

Any ideas?

Thanks in advance ;)

---

### Post by Robocoastie on 2006-03-24
ditto to the origin question. I made a post earlier and somehow missed this when I searched before making my post. Basically looking for the best kernel to use for my P4-HT-EM64T proc currently I'm running a xeon-smp one I found but I don't think its optimized as well. That em64t one origin poster mentioned failed for me with the same error he mentioned. Going to try the amd64-smp one next, recompile video again and try it.

---

