---
title: "installing ubuntu hp-printer problems and smp problems"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by rvdb on 2005-04-25
Dear all,

i've installed Ubuntu 5.04 and while doing so i scribbled down the following notes (see below). Maybe these are of some helpto someone, and maybe someone can help me solve the smp problem.

install printer HP Officejet G55

        - install hpoj, hpijs
        - turn printer off and on again
        - /etc/init/cupsys stop
        - ptal-init setup (and select the G55)
        - /etc/init/hpoj restart
        - /etc/init/cupsys start

install scanner

        - automatic with printer install


install nvidia driver

        - available in the rpm repository


smp kernel

        - installed the linux-686-smp package, but then the 
          mouse/keyboard did not respond anymore. So i;m running the 
          single processor kernel now...

Regards
Rein van den Boomgaard

---

### Post by poofyhairguy on 2005-04-25
[QUOTE=rvdb]
smp kernel

        - installed the linux-686-smp package, but then the 
          mouse/keyboard did not respond anymore. So i;m running the 
          single processor kernel now...

Regards
Rein van den Boomgaard[/QUOTE]

Have you tried the other 686 package? Does it work?

---

### Post by rvdb on 2005-04-25
[QUOTE=poofyhairguy]Have you tried the other 686 package? Does it work?[/QUOTE]
 Yes i now have have the linux-686 kernel package installed (from what i understand) and that one is running ok

Rein

---

### Post by dream.x on 2005-07-02
Same problem here, but only after installing and configuring hpoj, before it worked like a charm.

However, configuring hpoj via ptal-init setup, I chose to use HP usb drivers instead of the ones included in the kernel: is it possible that the problem is here?

Anyway, thanks to rvdb: I couldn't manage to install my OJ before reading your thread  \\:D/

---

