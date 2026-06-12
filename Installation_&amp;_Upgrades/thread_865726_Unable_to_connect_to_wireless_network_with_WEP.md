---
title: "Unable to connect to wireless network with WEP"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by osprey23 on 2008-07-20
Hi everyone,

I am new to Ubuntu and have just installed version 8.04.1 on my Pentium III 1GHz machine. Everything went nice, including the response of the OS on my machine.

The only problem (and happens to be the show stopper) is that my wireless network card is not able to get a connectin. I am using the Linksys WMP54G PCI card.

It seems like it is working, and I managed to configure the WEP HEX settings. But it just wouldn't connect to my wireless router.

Please see the lswh output below. Any comments or advise from anyone would be greatly appreciated.

BTW, I am not able to scan for wireless connections as well. When I execute "sudo iwlist scanning", it states that my wireless interface "wlan0" is not available for scanning.

Thanks.


```
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:74:46:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


```

---

### Post by poofyhairguy on 2008-07-21
You need to use NDiswrapper for that card. Here is a guide that should work on any recent Ubuntu.


[http://hehe2.net/linuxhumor/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/](http://hehe2.net/linuxhumor/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/)

---

### Post by osprey23 on 2008-07-22
> **poofyhairguy said:**
> You need to use NDiswrapper for that card. Here is a guide that should work on any recent Ubuntu.


[http://hehe2.net/linuxhumor/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/](http://hehe2.net/linuxhumor/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/)

I tried to compile the ndiswrapper, but it requires GCC which is missing, and I cannot find it. Is GCC is available on the 8.0.4 distribution CD?

---

### Post by Partyboi2 on 2008-07-22
> **osprey23 said:**
> I tried to compile the ndiswrapper, but it requires GCC which is missing, and I cannot find it. Is GCC is available on the 8.0.4 distribution CD?
Yes it should be on the ubuntu disk. If not you can download it from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/search?keywords=GCC&searchon=all&suite=hardy&section=all")

---

