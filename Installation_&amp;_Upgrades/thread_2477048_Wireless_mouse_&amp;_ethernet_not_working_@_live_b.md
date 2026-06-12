---
title: "Wireless mouse &amp; ethernet not working @ live boot"
date: 2022-07-13
forum: Installation &amp; Upgrades
---

### Post by slice3984 on 2022-07-13
Hi,
I tried to install ubuntu for dual boot with windows 10.
Booting into the live system resulted in my wireless mouse (Logitech g pro x superlight) and ethernet not working.
My previous attempt with xubuntu resulted in a working mouse (but not media controls using macros) and ethernet.
I also wonder if there are other recommendations for me for a distro, I'm a beginner, want to get used to linux and switch to i3wm when I got used to it.

My hardware:
Mainboard: Asus Strix X570-E
CPU: Ryzen 7 5800X
GPU: Nvidia RTX 2070S

---

### Post by grahammechanical on 2022-07-13
You do not say what version of Ubuntu you are using. From a Ubuntu/Xubuntu live session run this command

```
lshw
```

There will be a long printout. Look for something like this:

>   *-network
             description: Ethernet interface
             product: Ethernet Connection (10) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: enp0s31f6
             version: 00
             serial: 80:fa:5b:9d:b0:5c
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
              configuration: autonegotiation=on broadcast=yes driver=e1000e  driverversion=5.13.0-48-generic firmware=0.5-4 latency=0 link=no  multicast=yes port=twisted pair
             resources: irq:130 memory:b1400000-b141ffff

Notice that on my system there is a driver=e1000e. What do you see for your system?

The  reality is that Linux distributions rely on the Linux developers to  provide hardware drivers. The drivers come in a package called Linux  Firmware. If two distributions have the same Linux kernel then they also  have exactly the same hardware drivers. So what version of  Ubuntu/Xubuntu have you been trying? What Linux kernel.

```
uname -a
```

This is what I have.

> Linux  graham-Hybris 5.13.0-52-generic #59~20.04.1-Ubuntu SMP Thu Jun 16  21:21:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

Regards

---

