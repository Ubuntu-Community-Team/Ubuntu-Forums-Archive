---
title: "fglrx drivers finally work"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by waspbr on 2008-10-16
just wanted to spread the good news,  since there have been a ton of updates lately I decided that I should take the plunge and install the fglrx driver and :D they finally work on my radeon HD 3850 AGP.

---

### Post by Odur on 2008-10-16
Can someone please test if switching users works without a total freeze of the computer. I've tested this on Hardy with the new 8.10 (and 8.3 to 8.9) from AMD's site, and I got a total freeze when switching users. It's not the same bug as when the screen goes black on shutdown when atieventsd is running. I've already taken care of that one.

From my comment on Launchpad:
> Dist: Kubuntu 8.04.1 Fully upgraded
Graphics card: PowerColor (ATI) HD3870 SCS3
Tested drivers: fglrx 8.3 through 8.9

Symptoms: When switching user the screen goes black and the system is totally unresponsive, including the keyboard. Not even caps-lock trigges the caps-lock light. The only thing that works is the reset button and to hold the powerbutton until it shuts down. Shutdown or restart works without problem (I have fixed the problem with atieventsd, see bug 118605).
If i use the vesa or radeonhd drivers everything is ok. But then I got no 3D acceleration, which I think would be nice...

This bug is really annoying to me, as we are switching users a lot on this computer. It started when I bought this card. I got a ATI X600 before, and that didn't suffer from this bug at all.

---

