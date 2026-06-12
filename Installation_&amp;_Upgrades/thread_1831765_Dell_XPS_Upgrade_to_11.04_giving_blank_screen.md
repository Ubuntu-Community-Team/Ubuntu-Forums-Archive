---
title: "Dell XPS Upgrade to 11.04 giving blank screen"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by kw_martin on 2011-08-23
Monitor: AMD Radeon HD 6450

I got it working by in grub menu, first typing "e" to edit the first line, and then going to the line starting with "linux", and adding Vga=792, and then typing ^-X. This took a few hours of trial and error and forum searching to get to:):).

Next I went to System->Hardware->Additional Drivers and downloaded the ATI/AMD proprietary FGLRX graphics driver.

I also ran the update manager.

These seem to have fixed things.

---

