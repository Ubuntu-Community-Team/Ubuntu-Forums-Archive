---
title: "frame-buffer complete removal"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by costinc on 2006-11-19
Hello 

What options are to remove complete frame-buffer suport at boot or after init start ?

How I can block (framebuffer) modules load at startup ?

---

### Post by costinc on 2006-11-19
Fastest method to prevent fb modules to be loaded (in any way) at startup (by any services) is to comment lines that reffering to framebuffer aliases/drivers from /lib/modules/2.6.18-1-xen-686/
/lib/modules/2.6.18-1-xen-686/modules.alias:#alias pci:v000010DEd*sv*sd*bc03sc*i* nvidiafb

---

