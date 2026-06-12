---
title: "[SOLVED] Network recognized but not functioning"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by Guenter on 2007-12-28
Tried gutsy/hardy. have firewire / wlan / lan (rltk)

checked "dmesg" eth0 = lan

somehow it even manages to get an IP but it does not work. Can't ping any internal/external IP.

Debian/Other Distri works perfekt on that Laptop. But unfortuneatly x11 from debian does not work with my graphic card (ati) what does with ubuntu.

---

### Post by Pumalite on 2007-12-28
What do you get with:
ip addr
Also post:
lshw -C network

---

### Post by Guenter on 2007-12-29
funny thing, had problemes how to cap the results and post them in here without network ^^


anyway thank you very much for replying.

I installed again ubuntu/hardy this time alternate-iso -> expert mode. I did not get any errors during installation (even dhcp seems to work).

And yet network does not work. What I find a little disturbing, is that I can't choose the primary network between eth0/eth1 (firewire / lan) like I can under debian..


Anyway here the logs:
**ip addr**
```
[SIZE="2"]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:02:3f:b5:37:93 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.114/24 brd 192.168.2.255 scope global eth0
    inet6 fe80::202:3fff:feb5:3793/64 scope link 
       valid_lft forever preferred_lft forever
3: wmaster0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc ieee80211 qlen 1000
    link/ieee802.11 00:1a:4d:31:e6:eb brd ff:ff:ff:ff:ff:ff
4: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1a:4d:31:e6:eb brd ff:ff:ff:ff:ff:ff[/SIZE]

```

**lshw**

```
 [SIZE="2"] *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:b5:37:93
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.114 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: wmaster0
       version: 00
       serial: 00:1a:4d:31:e6:eb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
[/SIZE]
```

---

### Post by oldsoundguy on 2007-12-29
first clarify if you are trying to set up the eithernet (wired) or the wireless setup.

AND have you gone to System> Network> and hauled up the network settings screen and done the highlight/properties and done the do there?

Wired has been ZERO problems for my network .. just plug it in and boot up. NOTHING to install.

---

### Post by Guenter on 2007-12-29
wow.. wtf..

ok after some many hours spending @google ( :D ) I finally found the solution...

as I am too tired to tell the story of my life I will just give the plain solution... 

[http://ubuntuforums.org/showthread.php?t=310018](http://ubuntuforums.org/showthread.php?t=310018)

irqpoll was the keyword for my Fujitsu Amilo A 7600 (CY26)..

everything seems to work.. even my other usb slots without "hacking" the kernel.. thanks..

@oldsoundguy:
both didn't work and yep I've done all settings I could do ;), and yes again I am used to "plug&play" network config on debian/ubuntu, too - thats why I was so curious.. anyway thanks for reply.. problem solved

---

