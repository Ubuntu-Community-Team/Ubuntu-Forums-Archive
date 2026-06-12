---
title: "Karmic Mini ISO, no network drivers?"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kareeser on 2009-10-12
I'm not sure whether this is a bug or an isolated case with using the mini ISO... hence why I'm asking here and not Launchpad.

I installed Karmic using the minimal CD, and everything worked great - I got a minimal system, no fuss, no muss, and then I installed ubuntu-desktop on top of it... which seems a little redundant, but it was a new experiment.

In any case, Karmic started giving me trouble with my network card... it would be fine if it booted with the cat5 cable plugged in, but:
[list]
[*]Network manager refused to manage the device
[*]If I unplugged cable, the wireless would work, but I wouldn't be able to plug the cable back in to use a wired connection
[*]nm-applet didn't report "Auto eth0", it reported "ifupdown" as one of the networks.
[*]Randomly, eth1 gets renamed to eth1_rename, which wreaks havoc with /etc/network/interfaces on boot
[/list]

Am I missing a driver package for my card? (As always, Jaunty and other versions never had this problem...)

```
julian@kodaly:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:2a:0e:b2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.0.101 latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:81:6f:38
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:50:b5:23:d6:97
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by xebian on 2009-10-12
ubuntu-desktop is the same as installing from the full CD.

You should have installed mini.iso + ubuntu-minimal + packages you select,...,etc.

---

### Post by Corsair Freak on 2009-10-12
Where did you get a Karmic Mini.iso? I can only find the Jaunty Mini.iso.

---

### Post by xebian on 2009-10-12
> **Corsair Freak said:**
> Where did you get a Karmic Mini.iso? I can only find the Jaunty Mini.iso.

[http://cdimages.ubuntu.com/netboot/](http://cdimages.ubuntu.com/netboot/)

---

### Post by Kareeser on 2009-10-13
> **xebian said:**
> ubuntu-desktop is the same as installing from the full CD.

You should have installed mini.iso + ubuntu-minimal + packages you select,...,etc.

Hm, but even so, then I should have no problem with my ethernet/wireless card... something went wonky between Alpha 6 (last time I had Karmic) and now... since they worked fine back then.

---

