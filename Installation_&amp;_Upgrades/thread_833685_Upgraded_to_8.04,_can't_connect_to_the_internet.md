---
title: "Upgraded to 8.04, can't connect to the internet"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by Sherina on 2008-06-18
Hi 

So today I decided to upgrade from 7.10 to 8.04. I had no problems when I was using 7.10 but now in 8.04 I now have two major problems. The first problem is my graphics card (ATI radeon xpress 200m) was not recognized I fixed it but now my graphics don't run smoothly. The second and the biggest problem I have is that I can't connect to the internet(wireless). I am using an Intel Toshiba satellite laptop.

Thanks in advance.

---

### Post by circusmonkey on 2008-06-18
Neither can I after an upgrade when the help by default says it should connect automatically . 7.10 worked fine by default 
 
router/ hub netgear DG632, 7.10 worked by default.

R

---

### Post by Pumalite on 2008-06-18
Go to System>Administration>Software Sources>Open up (place a check) all your repos, including partner, proposed, backports, updates; reload.
Then:
sudo apt-get dist-upgrade
Report back.

---

### Post by Sherina on 2008-06-18
Pumalite I tryed what you said and it did not work. I did a system hardware check and it regonized my wireless card but when I click on the network icon it doesn't show me anything. Do I have to do a clean install in order to get everything to work?

---

### Post by Pumalite on 2008-06-18
Let's try something first. Post:
lshw -C network
ip addr

---

### Post by Sherina on 2008-06-18
*-network UNCLAIMED     

       description: Ethernet controller

       product: AR242x 802.11abg Wireless PCI Express Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:02:00.0

       version: 01

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list

       configuration: latency=0

  *-network

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 7

       bus info: pci@0000:0b:07.0

       logical name: eth0

       version: 10

       serial: 00:a0:d1:52:02:1a

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes





1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue 

    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

    inet 127.0.0.1/8 scope host lo

    inet6 ::1/128 scope host 

       valid_lft forever preferred_lft forever

2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000

    link/ether 00:a0:d1:52:02:1a brd ff:ff:ff:ff:ff:ff

---

### Post by Pumalite on 2008-06-18
Bad news; your Ethernet Controller is not recognized and the module not loaded. Try a clean install.

---

### Post by Sherina on 2008-06-18
ok, I had a feeling I was going to have to do that. how do I do a clean install without messing up my windows xp partion.

thanks

---

