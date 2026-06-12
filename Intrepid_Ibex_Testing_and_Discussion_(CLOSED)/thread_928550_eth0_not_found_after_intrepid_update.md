---
title: "eth0 not found after intrepid update"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by keletipu80 on 2008-09-24
Hello,

I am using the alpha version of intrepid, which worked fine so far. After updating this morning and restarting, my network connection does not work anymore.

```
sudo /etc/init.d/networking start
```

gives

```
eth0: ERROR while getting interface flags: no such device
SIOCSFADDR: No such device
...
Failed to bring up eth0.
```

Does anyone have any suggestions? Thanx.

---

### Post by pedro_orange on 2008-09-24
Hi,

You should really be asking this in the Ibex forums, since they will know more about it I'm afraid.

But you could try seeing if it recognizes the hardware with a:

```
lshw -C network
```

Although I doubt it will have assigned it a logical name if you've already restarted networking.

---

### Post by keletipu80 on 2008-09-24
This gives:
```

*-network UNCLAIMED
description: Ethernet controller
product: 82573E Gigabit Ethernet controller (Copper)
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0

```

---

### Post by pedro_orange on 2008-09-24
This may help:

[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/283000364931/r/889006564931](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/283000364931/r/889006564931)

So the driver may well be disabled

---

### Post by keletipu80 on 2008-09-24
Thanks Pedro for this info. For other users: To make a long story short, the driver has been disabled in the latest kernel, because it can damage your hardware. Booting with an older Kernel is a workaround, but puts your hardware at risk. This solves this issue for me.

---

### Post by shanix on 2008-09-24
And for anyone that would like to know more or experiencing this issue, here is the official bug report:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/263555)

---

