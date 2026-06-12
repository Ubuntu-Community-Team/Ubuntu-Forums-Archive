---
title: "linux-rt kernel sources"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by d_b on 2007-12-17
Hello everyone, 

I've been trying to get the sources to the linux-rt kernel image (2.6.22-14-rt specifically).  I need to recompile the kernel without a bunch of options and only the modules that I need for an embedded box that I'm building.

I've tried to install the "linux-sources" package, but it seems to get me the generic kernel (with no realtime preemption configuration options)

I've also tried: 

```
sudo apt-get source linux-image-2.6.22-14-rt
```

The result is a folder called linux-sources-2.6.22_2.6.22.  If I run ```
make menuconfig
``` using the options from my kernel (/boot/config-2.6.22-14-rt), I get a bunch of non-existent symbols errors, mostly related to the realtime preempt patch configuration options. 

How can I get the linux-rt sources with the -rt patch actually applied?  

I'm confused!  Any help would be much appreciated! 

d.

---

