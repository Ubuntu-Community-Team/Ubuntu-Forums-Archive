---
title: "Machine very slow with throtlling activation*: never come back to 100%"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by batmat on 2008-03-12
Hi all,

For 2 or 3 weeks now, I guess, my machine has a problem with performances, although the conf is quite correct imo: pentium M 1.6GHz, 1GB RAM, centrino laptop.
I upgraded from gutsy to hardy (the alpha version, yes). 

I noticed that at some point (when running some processor consuming processes), my machine suddenly went very very slow. So I looked for something suspect and I think I found the cause of the problem.

I already logged this problem in the ubuntu tracker but didn't have any answer until now: [https://bugs.launchpad.net/ubuntu/+bug/199391](https://bugs.launchpad.net/ubuntu/+bug/199391)

Here's the description of the bevaviour.
After bootup, everything is normal. The laptop fan is off. The throttling state is T0*:
baptiste@pumte:~$ cat /proc/acpi/processor/CPU0/throttling 
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

Then, when I start say firefox with some consuming flash in 5 or 6 tabs or start a video, my processor starts to heat. This seems normal, my processor temperature is about 40°C (looking at cat /proc/acpi/thermal_zone/THM/temperature).

When it reaches a little bit more than 70°C (I once read that a pentium M can go up to 90°C without any risk), it then switches to T6 mode and also activates the fan!

As you can see above, T6 is 25%, so my machine becomes almost unusable. 

The big point is that even if the tempature goes down back, thanks to the fan. Throttling mode will never come back to something upper than T6... 
Actually, I perfectly understand that switching to prevent damaging processor with too high temperature, when it comes back to something acceptable it then should automatically come back to state T0 (or even T1, T2 which I guess could be acceptable).

Btw, why T6 directly?

So, to sum up, what I'm looking is a way to configure my box to correct this behaviour. So that it comes back to some higher state after having lower the process temperature for example.

Any ideas*?

Cheers.

---

