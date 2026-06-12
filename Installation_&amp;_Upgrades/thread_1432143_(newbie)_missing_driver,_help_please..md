---
title: "(newbie) missing driver, help please."
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by ocurrente on 2010-03-17
hi! good day! newbie here!
I'm having some graphs troubles in Ubuntu 9.10, for example the videos go slow. 
I used the lshw -C display:
  ```
*-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:5 memory:e8000000-efffffff(prefetchable) memory:e0000000-e007ffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff(prefetchable) memory:e0080000-e00fffff
```I noticed that 'display:1' has not a driver installed. So, I went to [http://intellinuxgraphics.org/2009Q4.html](http://intellinuxgraphics.org/2009Q4.html), but I don't know what driver component I need,  and i went to [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html) but I don't know what installation process should I do, '2D only driver' or 'whole stack building' or another, if some one could help me with this would be great, because I don't want to mess my Ubuntu up.

I have kernel 2.6.31-20-generic

btw, sorry about my english.

---

