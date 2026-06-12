---
title: "lowlatency kernel xorg.conf settings are off"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by pixeltarian on 2007-09-28
is there a way I can copy the drivers and xorg.conf settings from my generic-kernel ???  the lowlatency version will not boot because there's a problem with the xorg.conf settings. 

exact versions: 
2.6.10-16-generic 
2.6.10-16-lowlatency

---

### Post by dcstar on 2007-09-29
> **pixeltarian said:**
> is there a way I can copy the drivers and xorg.conf settings from my generic-kernel ???  the lowlatency version will not boot because there's a problem with the xorg.conf settings. 

exact versions: 
2.6.10-16-generic 
2.6.10-16-lowlatency

Just make sure you have also installed the linux-restricted-modules and headers for the lowlatency kernel.

Nothing else should need to be changed.

---

### Post by pixeltarian on 2007-09-29
is there a way I can do that from the generic kernel?

---

