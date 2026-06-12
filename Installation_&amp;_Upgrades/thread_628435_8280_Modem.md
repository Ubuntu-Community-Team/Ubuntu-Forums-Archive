---
title: "8280 Modem"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by persisto on 2007-12-01
I have installed Ubuntu 7.10 on a USB drive connected to an ACER 5710z (of which the internal HDD/Controller does not work) This works very well (WIFI neede a bit of tweaking but now works)

The internal modem (56k) is not recognized. I have searched the forums and tried some of the suggestions, but I find the mesages produced by scanmodem confusing to say the least.

I believe to have understood that the modem is part of the functionality of Intel 8280 chipset of this machine.

Can some-one point me to the correct driver for this and the method of installing it?
(I am not a Linux expert)

Many Thanks in advance

Pete

---

### Post by Pumalite on 2007-12-01
Post:
lshw -C network

---

### Post by persisto on 2007-12-01
Thank for your answer:

```

magali@magali-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:22:29:1c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5787m-v3.22 ip=192.168.0.247 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:c9:d7:5a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
magali@magali-laptop:~$ 

```

---

### Post by Pumalite on 2007-12-01
Give me the brand and model of your internal modem.

---

### Post by persisto on 2007-12-01
Thats a bit of a Catch22! I do not know and can not find the specs for the modem. All I know is that the PC has a 8280 chipset (Acer 5710Z)

---

### Post by Pumalite on 2007-12-01
You have Ethernet and Wireless. What do you want the modem for...

---

### Post by persisto on 2007-12-01
Im at home, the PC belongs to a friend, who only has dial up. (I swear this is the truth, your honor)

---

### Post by Pumalite on 2007-12-01
Someone that knows more than I will chime in.

---

