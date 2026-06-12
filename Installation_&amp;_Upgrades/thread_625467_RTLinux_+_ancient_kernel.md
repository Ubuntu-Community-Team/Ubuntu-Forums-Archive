---
title: "RTLinux + ancient kernel"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by Ghyom on 2007-11-28
Hi everyone,

my goal is to install RTLinux in order to use a scientific application called Nspike ([http://nspike.sourceforge.net/](http://nspike.sourceforge.net/)).

Got the latest RTLinux (3.2) from rtlinuxfree.com. To install RTLinux, I need to patch my kernel sources and recompile the kernel. RTLinux 3.2 provides patches for kernels 2.4.X and 2.6.9 only. It looks like the patch for 2.6.9 does not work on kernels > 2.6.9.

I tried to recompile a kernel 2.6.9 on gutsy but 1) many errors and 2) it looks like a bad idea to go to a previous kernel on a recent distribution.

So I wanted to install a previous version (Hoary) to be able to recompile the 2.6.9 kernel. But many packages required for compilation can not be retrieved because some Hoary repositories are gone.

I guess I'll try Dapper and hope that the kernel 2.6.9 will compile.

Anyone would have another idea ? Another distribution ?

Cheers,

G.

---

### Post by jpkotta on 2007-11-28
Dapper might be a better idea, since it is supposed to be supported for 5 years (server).  What are the errors you get when compiling?  You're using kernel sources from kernel.org and not the Ubuntu repos, right?

---

