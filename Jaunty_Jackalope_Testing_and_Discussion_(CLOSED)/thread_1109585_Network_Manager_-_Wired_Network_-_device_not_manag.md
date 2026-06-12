---
title: "Network Manager - Wired Network - device not managed?"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JimTDI on 2009-03-28
Network Manager shows this error when I click on it, but it seems my wired network connection works?  The icon on the top bar also looks like there is a connection problem??

---

### Post by Kareeser on 2009-03-28
Ran into a similar problem with a broadcom 43xx card.

Run lshw -C network... what kind of card are you using?

---

### Post by zika on 2009-03-29
> **JimTDI said:**
> Network Manager shows this error when I click on it, but it seems my wired network connection works?  The icon on the top bar also looks like there is a connection problem??
make /etc/NetworkManager/nm-system-settings.conf to look like:
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

---

### Post by JimTDI on 2009-03-29
> **Kareeser said:**
> Ran into a similar problem with a broadcom 43xx card.

Run lshw -C network... what kind of card are you using?

It's an ethernet port off an Intel Pentium 4 motherboard, so it's not really a card.  I would assume it uses the Intel chipset.  Kind of disappointing since it's worked flawlessly in several other versions of Ubuntu.

Can you tell me the exact command to run you mention above?  The lshw one?  I get lost after the three dots after the word "network".

Thank you!

---

### Post by Quintilian on 2009-04-08
hi, i am having this trouble also. never noticed it before because i always used just the wireless, which works fine.

and to Zika: my /etc/NetworkManager/nm-system-settings.conf looks exactly the same as what you posted.

here is what i get when i run the command
shalwes@greyfox:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:a7:3b:8c:06
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=163.11.162.188 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:11:40:61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:68:44:61:5c:d6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


i realize the last one says disabled and it's supposedly a physical port (although i only have 1 physical port, just clarifying) but i dont know how to enable it or if thats even my problem.

also, is this just a problem with jaunty? i assume so, but o well

---

### Post by zika on 2009-04-09
> **Quintilian said:**
> hi, i am having this trouble also. never noticed it before because i always used just the wireless, which works fine.

and to Zika: my /etc/NetworkManager/nm-system-settings.conf looks exactly the same as what you posted.

here is what i get when i run the command
shalwes@greyfox:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:a7:3b:8c:06
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=163.11.162.188 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:11:40:61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:68:44:61:5c:d6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


i realize the last one says disabled and it's supposedly a physical port (although i only have 1 physical port, just clarifying) but i dont know how to enable it or if thats even my problem.

also, is this just a problem with jaunty? i assume so, but o well
try changing *managed=false* to *managed=true* if You want NM to manage Your wired. In JJ things settled and I, for now, on all 4 machines, do not have anything else but NM ... :)

---

### Post by opt on 2009-04-13
Hi, I had the same problem with Jaunty. Wireless was working through ndiswrapper (with b43 couldn't connect to WPA encrypted networks). Then wired network suddenly didn't work. I noticed that the problem was that b44 module wasn't loaded. sudo modprobe b44 fixed the wired problem. I have a Dell Vostro 1700, with Broadcom network cards.

---

### Post by SAPnet on 2009-04-20
I had the same problem with the wired connection after upgrading from 8.10 to 9.04 RC.

Changing [ifupdown] managed=false to true in /etc/NetworkManager/nm-system-settings.conf resolved the issue.

---

### Post by Quintilian on 2009-04-20
thanks everyone, i got it working now! :D

---

