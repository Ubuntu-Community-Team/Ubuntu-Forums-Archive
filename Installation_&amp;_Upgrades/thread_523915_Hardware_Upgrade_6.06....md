---
title: "Hardware Upgrade 6.06..."
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by mo1tomax on 2007-08-12
How much pain will I inflict on myself if I swap out my MOBO, containing an AMDk7 750, 390MB SDRAM, and a VOODOO 5 (AGP) - VIA chipset - for one containing an AMD64 (3200+), 1GB DDR2, and an NVIDIA FX5200 (AGP) - VIA chipset.  I am currently using the Ubuntu 6.06.1 LTS with linux-image-server in a LAMP configuration.  I have not re-compiled the kernel.

---

### Post by Pumalite on 2007-08-12
Some say the kernel loads the modules necessary for the hardware upon boot. I'm not so sure. Maybe somebody else is more sure about this.

---

### Post by mo1tomax on 2007-08-12
I searched the available packages using Aptitude for a specific 64-bit package of the kernel and found none.  It sounds plausible that a simple swap would cause limited damage - more worried about the GFX cards.  I may just try it and find out what hoops I need to jump through.  Is there a way of finding out what modules are available to the kernel by default?

---

### Post by Pumalite on 2007-08-12
Sorry, but I have no idea of 64 bit. Somebody will jump in.

---

### Post by mo1tomax on 2007-08-14
I made the hardware change and it went without issue.  Now... 
**How do I convert the active system to 64-bit?**

Thanks

---

