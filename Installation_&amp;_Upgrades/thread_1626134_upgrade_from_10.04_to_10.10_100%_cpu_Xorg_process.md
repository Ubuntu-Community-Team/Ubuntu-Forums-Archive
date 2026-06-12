---
title: "upgrade from 10.04 to 10.10 100% cpu Xorg process"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by aarons6 on 2010-11-19
my computer is unusable.. every time i click or open or move a window it freezes for several seconds. system monitor shows at this time the process Xorg is using 100% cpu.


it never drops down below 40%, even at idle.

my system is amd 64 4000+ 3gb ram and ati 3650 HD video.

i have kubuntu 64 10.10 with all the updates and default ati drivers.

---

### Post by mörgæs on 2010-11-21
How does 10.10 work when booted from a live CD?

---

### Post by sikander3786 on 2010-11-21
Instead of running System Monitor, try the top command from terminal. (System Monitor itself uses up a lot of resources for graphs and all that).

And try to reconfigure your graphics by

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You mentioned default ATI drivers, I assume you mean the open source drivers. If thats the case, installing the proprietary drivers might help. System > Administration > Additional Drivers.

Good Luck!

---

### Post by aarons6 on 2010-11-24
nothing seemed to help, had to go back to 10.04

---

### Post by aarons6 on 2010-11-24
> **mörgæs said:**
> How does 10.10 work when booted from a live CD?


this does not use the ati drivers, so it runs normally.

---

### Post by mörgæs on 2010-11-24
Good, please mark the thread 'solved'.

---

### Post by aarons6 on 2010-12-04
Its not solved. 10.10 will not run on my PC.
I had to reformat and go back to 10.04.

---

