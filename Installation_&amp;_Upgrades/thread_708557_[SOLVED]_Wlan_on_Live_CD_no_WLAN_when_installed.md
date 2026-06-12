---
title: "[SOLVED] Wlan on Live CD no WLAN when installed"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by thusgaard on 2008-02-26
Hi 

When testing Mythbuntu 7,10 on my HP mediacenter, WLAN worked flawlessly.
So I installed, now I have no WLAN. 

How do I get WLAN back?
How do I get a print of my hardware configuration?

J;-)

---

### Post by Partyboi2 on 2008-02-26
[This]("http://ubuntuforums.org/showthread.php?t=571194") might help to troubleshoot

---

### Post by thusgaard on 2008-02-27
How do I enable my wireless?


*-network:1 DISABLED
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 4
       bus info: pci@0000:03:04.0
       logical name: eth1
       version: 01
       serial: 00:30:b4:00:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 driverversion=1.2 latency=64 maxlatency=28 mingnt=10 module=prism54 multicast=yes wireless=NOT READY!


J;-)

---

### Post by thusgaard on 2008-02-27
This it how it looks when I boot from Live CD. It works when it looks like this:

*-network:1
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 4
       bus info: pci@0000:03:04.0
       logical name: wmaster0
       version: 01
       serial: 00:12:bf:02:db:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=prism54pci latency=64 maxlatency=28 mingnt=10 module=p54pci multicast=yes wireless=IEEE 802.11g

---

### Post by thusgaard on 2008-03-03
I solved my problem. With the help of all the above.

First I did a:
```
sudo rmmod prism54 
```

The I did a, to make sure that the prismdriver was disablet:

```
lshw -C network
```

Then I blacklisted the driver I knew that didn't work, I opened the blacklist in gedit:

```
sudo gedit /etc/modprobe.d/blacklist
```

And added the folowing lines:

```
# Drivers I just dont like
blacklist prism54
```

Not knowing what to do when I want to add a module to the kernel (modprobe wouldn't work for me) I simply booted the PC. 

Now my:

```
lshw -C network
```

Looks like this:

```
  *-network:1
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 4
       bus info: pci@0000:03:04.0
       logical name: wmaster0
       version: 01
       serial: 00:12:bf:02:db:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=prism54pci ip=192.168.1.35 latency=64 maxlatency=28 mingnt=10 module=p54pci multicast=yes wireless=IEEE 802.11g
```

Thanks to partyboi2, for pointing me in the right direction, and still leaving it up to me to solve my problem.

J;-)

---

