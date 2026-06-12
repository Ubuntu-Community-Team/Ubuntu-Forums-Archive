---
title: "Suspect 2.6.31-13 ondemand not working"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gmc on 2009-10-12
I have a sneaky suspicion that the ondemand cpu module is not working in 2.6.31-13 kernel. I just converted an ogg to mp3 and back on my eeepc 1000he (Atom 280) and noticed that at no time during the operation did the CPU kick up to 1.6Ghz.

I double checked with cpuburn and with two instances running, again the cpu remained at low speed.

Can someone out there with either a C2D or an Atom based processor, try the cpuburn test and let me know if your cpu clocks up and down? Otherwise, I'll post a bug on Launchpad

Thanks
G

---

### Post by jmmL on 2009-10-12
I've got a C2D T5450 - burnMMX bumps it up from 1GHz up to its maximum 1.67GHz clock frequency.

---

### Post by bollix47 on 2009-10-12
I noticed similar behaviour when running Folding@Home.  CPU stayed at lowest Ghz(1.6).  I turned off speedstep in the bios and it runs at normal GHz(2.53).  Will be checking out cpufreq soon to see if that manages the situation better.

Also, this could be caused by heat issues which I will also be looking into. ;)

---

### Post by gmc on 2009-10-12
> **jmmL said:**
> I've got a C2D T5450 - burnMMX bumps it up from 1GHz up to its maximum 1.67GHz clock frequency.

Hmm... maybe it's something to do with my eeepc then. Much appreciate your time and effort, I'll wait a bit before bothering the Ubuntu kernel developers with this one.

Thank You

G.

---

### Post by gmc on 2009-10-12
:eek:

My BAD! I just checked my rc.local file (which I was using on Jaunty) and realized that I was tweaking the ondemand kernel module with wildly bad values. It's not a bug, it's a user error.

Sure glad I waited before posting to launchpad.

Thanks
G

---

