---
title: "Ubuntu keeps freezing"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by Bicky on 2005-11-13
I'm tryin to fix this problem for a long time now. But it keeps freezing.
When I'm using ubuntu it suddenly freezes (and somethimes even my mouse is gone). The only thing what I can do then is reset the computer.

specs:
AMD athlon thunderbird 1.4ghz
nvidia gforce 2 (drivers installed)
EP-8kta3 mainboard

Bicky
(don't know if I'm in the right subforum)

---

### Post by pmjdebruijn on 2005-11-14
Try the following:

Add 'mem=nopentium' at the end of the kernel line of the grub.conf file...

And configure UC instead of UCSW in the BIOS AGP section...

Regards,
Pascal de Bruijn

---

