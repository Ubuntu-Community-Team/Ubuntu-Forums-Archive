---
title: "Upgrade wtih Alternate CD"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2007-04-26
I finally have a good Alternate CD.  

I thought all that had to be done is boot 6.10, put in the CD, and an upgrade will be offered.  All that happens is that the contents are listed in File Browser.  When I try to run the CDROMUPGRADE", nothing happens.  It asks me if I want to run it, I answer YES, the box disappears, and ... NOTHING HAPPENS.

There must be something simple I'm missing, but I have no idea what.

---

### Post by zvacet on 2007-04-26
```
gksu "sh /cdrom/cdromupgrade" 
```

---

### Post by engine on 2007-12-27
> **zvacet said:**
> ```
gksu "sh /cdrom/cdromupgrade" 
```
Looks convincing, but for the timorous and fearful among us (and for other people seeking enlightenment), how does one use Synaptic to run an upgrade from an Alternate CD?

Thanks in advance!

---

