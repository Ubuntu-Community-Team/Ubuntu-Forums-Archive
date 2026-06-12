---
title: "Strange vga problem"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by doomlover on 2008-04-22
I have ubuntu 7.10 live cd and a weird vga problem...
I boot my pc with the cd, select "start or install ubuntu" and during the initial loading proccess my screen becomes scrambled. After this displays the message "h.v frequency over range" and suspends... i can hear the cd spinning, but the screen is off. I tried every possible resolution and the "safe graphixs mode" option. What can i do to solve this? I have a viewsonic e50 on a nvidia 7600GT vga, which run perfect on windows xp.

---

### Post by dstew on 2008-04-23
At the opening menu, press F6 to enter kernel options. Try the option **vesa=force** added at the end of the kernel line.

---

