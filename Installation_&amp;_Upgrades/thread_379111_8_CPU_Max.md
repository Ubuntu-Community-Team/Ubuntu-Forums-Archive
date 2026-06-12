---
title: "8 CPU Max?"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by bexamous on 2007-03-08
Why does the Install CD / Live CD only support 8 CPUs?

/proc/cpuinfo shows 16 cores total
top however will only say there are 8 CPUs

Is this because the kernel was set to 8 CPUs max?  This seems (annoyingly) wierd.  Are all the LiveCD/InstallCD kernels the same?

Any easy way to update the Install/LiveCD to work with 16 CPUs?  I don't get why the stock kernel won't work though.  Ubuntu have anything like genkernel for Gentoo?  I want to still have a very universal kernel because we use these CDs on a bunch of systems.  I've never actually tried to update a LiveCD's Kernel...  doesn't sound like something that will go smoothly.

---

### Post by Jussi Kukkonen on 2007-03-08
> **bexamous said:**
> Why does the Install CD / Live CD only support 8 CPUs?

/proc/cpuinfo shows 16 cores total
top however will only say there are 8 CPUs

Is this because the kernel was set to 8 CPUs max?  This seems (annoyingly) wierd.  

File a bug. This is probably just a mistake as even the kernel config comments say: 

> **NR_CPUS**
...
This is purely to save memory - each supported CPU adds
approximately eight kilobytes to the kernel image.

---

