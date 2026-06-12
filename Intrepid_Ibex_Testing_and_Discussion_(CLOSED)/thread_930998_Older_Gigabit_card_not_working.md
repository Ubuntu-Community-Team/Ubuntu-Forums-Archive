---
title: "Older Gigabit card not working"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by m0ntels on 2008-09-26
Had some minor issues with my Hardy install and I made the noob mistake of thinking an upgrade would replace anything I had messed up.

Intrepid boots up ok aside from sometimes not liking my nvidia card, but otherwise all seems to work except my network card.  It says networking is enabled on the panel icon and it lists eth0 and eth1, but I cant connect to the net.  I'm currently running a live cd so I can post.

Here is the result of "lshw -C network" from the live cd.

*-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:0e:a6:a4:0d:55
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth1
       version: 13
       serial: 00:0e:a6:a4:19:e3
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A ip=68.80.109.229 latency=32 maxlatency=31 mingnt=23 module=skge multicast=yes

I saw that some of the other Gigabit cards were having issues with Intrepid, but it looks like mine isn't one of the ones in the bug report.  Any tips?

---

