---
title: "Upgrade hangs on login"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by rnrralston on 2008-05-09
I allowed the latest upgrade to proceed on my Dell 800 laptop.  Unfortunately, things have not gone well.  The upgrade seemed to go off without a hitch, but after logging on the brown desktop shows and nothing else.  Clicking on the right location causes actions to take place, but it's pretty tough to hit the right spot if you can't see what to click!

It logs on OK in safe mode, but wireless doesn't work.

Is there any alternative to saving what data I can and a clean install?

---

### Post by Treutwein on 2008-05-09
I had a similar problem, and I'm not shure if my solution is the correct one ... 

After awful long wait my desktop appeared, but it was really frustrating. Console login was possible, but also very very slow. Glancing over the output of dmesg I saw an error "mtrr: no more MTRRs available".

I tried to chose the other available kernel (2.6.15-51-386) on the next reboot and the system appeared to be usable again. So I went to Grub's boot configuration and forced the system to boot the old kernel (i.e., menu entry 2 instead of the default 0). 

With this configuration, the system is at least usable, although there are several failed messages during boot.

regards
      Bernhard

---

