---
title: "Black screen after GRUB, fixed by hard reset"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Yako on 2010-03-31
Whenever I boot up my HP dv1668ea, it gives me a black screen right after GRUB. No messages at all, not even fsck. This screen will not go away and I can not use the computer. A reboot gives me the same results.

The only thing that fixes it is if i disconnect the power and remove the battery. When I put the battery back and start up, the system boots normally. But on next reboot I get the black screen again.

Maybe this has something to do with Plymouth and graphics modesetting. I think the video settings only get erased when I cut off the power completely.

This is on a fresh 10.04 beta install (with latest updates). Also, regulary it gives me a crash report about "plymouthd".

Specs:
HP dv1668ea
Intel GMA 945
2GB DDR2 RAM
Intel Core Duo 1,67GHz
Intel Postville X25-M 80GB SSD
Intel Pro/Wireless 3945

---

