---
title: "Upgrading to Edgy -- fixed &quot;jumpy&quot; mouse, video glitches"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by Gianni Exile on 2006-11-07
Hi,

I did a manual upgrade, Dapper to Edgy, little glitches I fixed no problem.  The BIG annoying glitch was that the mouse seemed "jumpy", tracking wasn't smooth.  Then video showed the same problem, jittery or pausing, and soon I realized the whole system was freezing for some microseconds every 3 to 5 seconds.

Solution?

I killed the processes one by one, and tried different (custom) kernels, until **ifplugd** was gone, and the system returned to normal smooth operation under any kernel.  I am used to manual reset/config of the networking in any case, so it's no loss to me.  I just thought I'd post this since it took a while for me to track down, and I've been using Linux since 1993.

Hopefully this can save someone some time.

The laptop I used for this upgrade is a 1MHz pentium III machine.

---

