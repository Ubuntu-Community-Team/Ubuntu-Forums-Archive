---
title: "eth0: ERROR while getting interface flags: No such device; Failed to bring up eth0."
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TwoOhFour on 2009-04-01
[FONT="Arial"][SIZE="2"]I just installed Ubuntu Server 9.04 Beta on a Compaq Proliant ML330 G2 server.
My problem is, it will not connect to my network.
I tried setting the IP to static, I got an error so I tried to change it to DHCP and I still got the same error. The error follows:

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

I can see the DHCP readout from /etc/init.d/networking restart so DHCP is trying to receive the information.

Running a ping of my switch gives me this:

connect: Network is unreachable

I have tried runnning 6.04 and 8.10 and they both have their own problems on this system during the installation, 9.04 at least gives me a system I can boot into and log in.

Any suggestions on how to fix this?

By the way, a physical inspection of the server shows that the lights on the NIC are on, so they cable and connection is good, the switch also shows that the cable is connected on both ends. I don't think it's a hardware problem; Ubuntu just isn't picking up the card. I'm no Linux developer, so I could be wrong.[/SIZE][/FONT]

---

### Post by chili555 on 2009-04-01
May we please see the following:```
cat /etc/network/interfaces
sudo lshw -C network
```Since this is a server and you have no network, how are you administering it? Did you simply attach a monitor, keyboard and mouse?

---

### Post by TwoOhFour on 2009-04-01
Last first, yes, I have a 17" LCD and keyboard and mouse on a table in front of it.

cat /etc/network/interfaces:

# This file describes ...
# and how ...

# The loopback ...
auto lo
iface lo inet loopback

# The primary ...
auto eth0
iface eth0 inet dhcp

sudo lshw -C network:
*-network UNCLAIMED
description: Ethernet controller
product: 82557/8/9/0/1 Ethernet Pro 100
vendor: Intel Corporation
physical id: 4
bus info: pci@0000:00:04.0
version: 08
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=64 maxlatency=56 mingnt=8

I have never used that command before, learning something all the time I suppose. Hope that helps.

*-*-*-*-*-

I did some Google searching and all I came up with was this forum topic and some info on this forum about the same kind of problem but with a wireless card.

---

### Post by TwoOhFour on 2009-04-02
Any ideas anyone?

---

