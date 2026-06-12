---
title: "Can I share Swap partition"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by bogey on 2006-10-31
I like trying out different Linux distros, in addition to Edgy.  Can I use the same Swap partition for each one, or do I need to create a separate Swap partition for each one?

---

### Post by _lynX on 2006-10-31
> **bogey said:**
> I like trying out different Linux distros, in addition to Edgy.  Can I use the same Swap partition for each one, or do I need to create a separate Swap partition for each one?
You should be able to use the same swap partition for each one.

---

### Post by bogey on 2006-10-31
Gracias.  That will clean up my partitions nicely.

---

### Post by amo-ej1 on 2006-10-31
the only thing that you should keep in mind is that that will break hibernating (if you make use of it). since hibernates writes the physical ram contents to the swap partition and resumes from there. 
but in any other case, go right ahead ;)

---

