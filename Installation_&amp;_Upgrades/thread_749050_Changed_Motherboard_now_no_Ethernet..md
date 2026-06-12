---
title: "Changed Motherboard now no Ethernet."
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by Raymond Day on 2008-04-08
I been running Ubuntu 7.10 server for a long time on a old mother board and it runs 24/7. So I wanted to get a small mother board to replace it that don't take a lot of power. I have a lot installed on it.

It's a 750GB hard drive. The new Mother board is a Intel Mini-ITXD201GLY2 and it has a Broadcom on board Ethernet. The old one had a Realtek Ethernet controller.

It boots up and looks like it works in the new mother board. But I can not ping it.

I can't type in it ether. Because on boot on the **old or new **mother board it stops at:

```
Running local boot scripts (/etc/rc.local)
``` with a flashing _ and no commands do any thing but show just stuff on the screen when I type. I guess if I could fix that I could run some command to get the Ethernet working.

Should it auto know the new Ethernet and work with it? I even put another ethernet card in it's one PCI slot but I still could not ping it.

I hope some one can help.

-Raymond Day

---

### Post by Raymond Day on 2008-04-08
I just got it working.

In the file at:

/etc/udev/rules.d/70-persistent-net.rules

I put it's MAC address in there. I got it from booting with no hard drive and it shows it's MAC address.

So it looked like this:

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="**:**:**:**:**:**", ATTRS{type}=="1", NAME="eth0"

I put * in place of the numbers. I don't know if it's good to post my MAC address.

It's did shows it's MAC address any way in there as eth1 so it did see it but just did not use it till I put it's MAC address in the 1st part in that file.

I guess this will help some others if they run in to this.

I would still like to fix the screen so I get the command prompt back. If any one knows a fix for that. But I can log in with putty over the Ethernet now.

-Raymond Day

---

