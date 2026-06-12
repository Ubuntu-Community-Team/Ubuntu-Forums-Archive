---
title: "Wired ethernet connection."
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2009-10-15
After having problems getting connected to my home network after upgrading my desktop, I decided to try wicd in case the problem was to do with Network Manager. My problems still persist (connection keeps dropping), but I also noticed something else. Wicd reports on startup that it connected to a wired connection, yet although I have   an ethernet port on my motherboard, it is not plugged into anything. Is there a way to tell if this is a bug, or have I had a problem during an update(because connection keeps dropping, I am not sure if I have had a corrupted download).

---

### Post by celticbhoy on 2009-10-15
just noticed that my ethernet adapter is listed in iwconfig & iwcd as virbr0, and any other system I have used has eth0, is this right?

---

### Post by Peter09 on 2009-10-15
I think that virbr0 is a bridged device - are you  using any virtualisation software?

---

### Post by celticbhoy on 2009-10-15
No straight install upgraded at weekend.

---

### Post by tekstr1der on 2009-10-15
What's type of NIC?

```
lspci | grep [nN]et
```

or

```
sudo lshw -c network
```

---

### Post by celticbhoy on 2009-10-15
01:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

Thats all that shows.

---

### Post by celticbhoy on 2009-10-15
*-network               
       description: Wireless interface
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:16:0a:00:28:3f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=p54pci ip=192.168.0.2 latency=96 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:e0000000-e0001fff


For second command.

---

### Post by tekstr1der on 2009-10-15
Certainly looks like a bridged connection. You'll run into all sorts of problems bridging to a wireless NIC. If you are not running any virtualization, this is odd. Also, the fact that your wired LAN adapter is not listed is disturbing. Did you disable it in the BIOS? Perhaps you managed to bridge your wireless to your wired adapter?

---

### Post by celticbhoy on 2009-10-15
Its not disabled in BIOS, and I have not messed about with any of the network interfaces. Everything was working fine under Jaunty, after upgrading I started to get connection problems, not just with PC, but also problems with my broadband line at the time. Is there any way to remove this driver? 

If I disable the ethernet connection from BIOS, will this solve the problem? If it thinks it is a virtual connection can I just break the link somehow?

---

### Post by celticbhoy on 2009-10-15
OK I have tried disabling & then re-enabling the ethernet from BIOS, and now my system shows the eth0 adapter. But the virbr0 is still showing, how do I remove this?

---

### Post by celticbhoy on 2009-10-15
Part solved now, I have set the wired adapter in wicd to use eth0, but virbr0 still remains. At least I get connected on startup now.

---

