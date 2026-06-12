---
title: "et131x driver won't compile?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by noctis_vulpes on 2008-04-26
Man, it's tough upgrading after using a setup for so long.

Right now, I'm trying to get my 8.04 set up on an LG notebook that I have, which uses the et131x driver for its ethernet connection. I was about to find the source for it in Synaptics, so I downloaded it and tried to compile it as I have with Feisty. However,  make fails with the following error:

```
/usr/src/modules/et131x$ sudo make
#@make -C /lib/modules/2.6.24-16-generic/build M=/usr/src/modules/et131x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /usr/src/modules/et131x/ET1310_rx.o
/usr/src/modules/et131x/ET1310_rx.c: In function ‘et131x_rx_dma_memory_alloc’:
/usr/src/modules/et131x/ET1310_rx.c:536: error: too many arguments to function ‘kmem_cache_create’
/usr/src/modules/et131x/ET1310_rx.c: In function ‘nic_rx_pkts’:
/usr/src/modules/et131x/ET1310_rx.c:1670: warning: unused variable ‘vlan_tag’
make[2]: *** [/usr/src/modules/et131x/ET1310_rx.o] Error 1
make[1]: *** [_module_/usr/src/modules/et131x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
```

does anyone have any idea what's going on? Feisty with the 1.2.3 driver didn't give me any problems.

Thank you in advance for any help.

---

### Post by noctis_vulpes on 2008-04-28
*bump* sorry, I'm still trying to get this to work... Has anyone had any success in compiling this same driver under 8.04?

---

### Post by rla3rd on 2008-05-12
I just patched the source to fix the problem.  you can download the latest source at:

[http://sourceforge.net/projects/et131x]("http://sourceforge.net/projects/et131x")

---

