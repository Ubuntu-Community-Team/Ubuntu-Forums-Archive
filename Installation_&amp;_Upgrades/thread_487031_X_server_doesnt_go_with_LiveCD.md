---
title: "X server doesnt go with LiveCD"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by qaws on 2007-06-28
After start from Live CD and safe graphic mode PC writes this:

[img]http://img216.imageshack.us/img216/6053/img8851kn8.jpg[/img]

VGA integrated: VGA compatible controller: Intel corporation 82835G/GL

Ubuntu 7.04 x86, I have tried also Ubuntu 6.06 x86, there is the same problem.

Sudo dpkg-reconfigure xserver-xorg ran, but startx did not go because: Fatal IO error. Connection reset by peer.

---

### Post by sharke on 2007-06-28
reconfigure xserver and choose vesa driver.
Regards
Sharke

---

### Post by Pumalite on 2007-06-28
Try 'Alternate CD'. How much memory do you have? Post your specs. Are you dual booting?Vista, XP or other Linux?

---

### Post by qaws on 2007-06-29
> **Pumalite said:**
> Try 'Alternate CD'. How much memory do you have? Post your specs. Are you dual booting?Vista, XP or other Linux?
I have new PC (from Dell)- there is installed only DOS now, so I dont know, whether is there nvidia or ati. It has 256MB of memory, 32-bit 1.8GHz Intel CPU and integrated graphic card. 

I have tried reconfiguring x-server and nv, ati and vesa driver, but there is still the same problem > Fatal IO error. Connection reset by peer.

I will try install from minimal CD.

---

### Post by Pumalite on 2007-06-29
Your problem is your low memory, therefore>'Alternate CD'. But at this point I have to advise you to go with the Xubuntu Alternate CD ( lighter Desktop and lighter memory usage). The Alternate Ubuntu would barely fit in there and still give you problems.

---

### Post by qaws on 2007-06-29
OK, thx, it runs with AlternateCD.

---

