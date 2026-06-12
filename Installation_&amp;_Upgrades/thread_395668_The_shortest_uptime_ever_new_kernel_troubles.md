---
title: "The shortest uptime ever: new kernel troubles"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by mahy on 2007-03-28
Hello everybody,

i chose to compile and install the new 2.6.20.4 kernel. Unpacked it to /usr/src, loaded the config file from the default kernel, changed the CPU type and set support for ReiserFS. Nothing else. Then i ran

make && make modules_install && make install

and edited the menu.lst to include it. After reboot, i selected the new kernel, the screen went black and blank, and after approx. 3 secs my laptop shut down. WTH?! No kernel panic, no nothing.

I also tried the same process without loading existing configuration. The results were similar, but the blank screen persisted (no shutdown).

I guess there's some devilry going on. Know any caveats? Or can you at least give me some nice and comprehensive howto? Please people, do help me. TIA

---

