---
title: "kernel in 8.10 xen enabled &quot;-generic&quot;?"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by slanbarn on 2008-11-03
Okey, so I did an 'apt-get dist-upgrade' to intrepid after altering my sources-list accodingly, that is replace hardy wit intrepid everywhere. 

Everyting worked nicely, reboort was OK, and so... But for some reason the current nvidia-driver(177.80) didnt work that well, the resolution for my tv is not working anymore, there is no pixel-mapping and the colors are all wrong. The correct resolution is 1360x768m this is the one that dont work, but 1024x768 is working OK except the screwed aspect....

So to the problem: I tried to install an older version of the nvidia-driver(177.70) but the installer says Im using a Xen-anabled kernel... First of all; WTF?!?!?!! A kernel named "-generc" that is xen-enabled?!? and for second, how to install the "same" kernel that is not xen-enabled to try with the older nvidia-driver? With the same I mean, with all the other features enabled, just not xen...? 
here is my 'uname -a':
```

uname -a
Linux ubuntu 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux

```

```
cat config-2.6.27-7-generic | grep XEN
CONFIG_HVC_XEN=y
CONFIG_NETXEN_NIC=m
CONFIG_XEN=y
CONFIG_XEN_BALLOON=y
CONFIG_XEN_BLKDEV_FRONTEND=m
CONFIG_XEN_FBDEV_FRONTEND=m
CONFIG_XEN_KBDDEV_FRONTEND=m
CONFIG_XEN_MAX_DOMAIN_MEMORY=32
CONFIG_XEN_NETDEV_FRONTEND=m
CONFIG_XEN_SAVE_RESTORE=y
CONFIG_XEN_SCRUB_PAGES=y

```

---

### Post by aurelieng on 2008-11-03
The server kernel of 8.04 have also xen enabled by default, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224340](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224340) 

It might be worth a bug report.

---

### Post by slanbarn on 2008-11-04
Yeah okey, I will see if can manage to report this as a bug, but in the meantime, is there a up-to-date feture-wise kernel(2.6.27) for 8.10 that is not xen-enabled that one can install? or is it debian lenny-time again? :)

---

