---
title: "problem with keyboard"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by t85us on 2010-03-25
Hi everyone!

I really don't know, if i messed up something in my ubuntu, but sometimes when i restart my computer (or when i turn it on and start) my keyboard does not work at all. I can press whatever i like, it won't answer (not even to alt+f1, alt+f2 too, or other "ctrl+alt+F", "ctrl alt del"). When i remove it, and plug it back, it will work without a problem. My keyboard is a USB type (microsoft wired keyboard 600 series with german layout). Checked, and when i simply reboot, works up until GRUB (and even in GRUB). This keyboard worked well in 9.10, i have trouble only in this new, 10.04 version.
Any suggestion ? 

My specs :
Ubuntu 10.04 amd64 alpha 1 
Kernel version 2.6.33-020633-generic
Athlon X2 5000+, Asrock K10N78, Radeon HD4850 (with "radeon" driver in xorg.conf)

---

### Post by dino99 on 2010-03-25
Several people have issues with freezes due to plymouth or else. You might look at your logs (/var/log or system admin log viewer), xorg.0.log might have some info

---

