---
title: "gutsy troubles"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by maarten12 on 2007-11-23
hello there,
I just installed a shiny new Ubuntu 7.10 gutsy gibbon and I have some troubles.
I have a multi boot with my Ubuntu and win XP and when I select Ubuntu, the screen stays black for about 1-2 minutes. during this time i can press Alt+F2 so I start something. then, something appears saying intel_rng: FWH not detected...
after this "delay" everything works fine. 
I think it has something to do with either my chipset (i915) or my WLAN cart (Intel 2200BG) 
how can I solve this problem? is it solvable actually?

---

### Post by derby007 on 2007-11-23
Its a bug at : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/102982]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/102982")

Related to wiireless....
Some workarounds seem to be : blacklisting it in /etc/modprobe.d/blacklist

---

