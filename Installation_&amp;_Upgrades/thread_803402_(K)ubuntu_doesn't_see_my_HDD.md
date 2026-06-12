---
title: "(K)ubuntu doesn't see my HDD"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by kamil_w on 2008-05-22
Hi Everybody,
I would like to install Kubuntu on my PC, but I can't. :(
I am booting Kubuntu LiveCD on my PC and everything is ok, but when I want to install it on my PC the installer doesn't see my hard drive. On step 4 in which I should prepare partitions there is only empty window and I can't go to the next step.

Moreover I tried to install Mandriva, openSuSE, Debian and I also can't install them. But, what is quite strange for me, Gparted form LiveCD and RescueSystem CD are working fine. I am also able to install Arch Linux.

The problem appeared when I have changed my Motherboard and HDD.
Now I have:
HDD: SATA 300 WD Caviar 250GB
Motherboard: Abit IB9 with ICH8 controler

Please tell me how to install Kubuntu

---

### Post by dstew on 2008-05-22
There may be a [kernel bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/172300") relative to that motherboard. A possible workaround is to add the parameter **irqpoll** to the kernel line. I think you press F6 at the opening menu to add kernel parameters. Add **irqpoll** to the end of the line, press enter, and continue booting.

---

