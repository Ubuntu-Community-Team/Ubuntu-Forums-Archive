---
title: "Hardy not recognising wireless card but xubuntu does"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by tipiglen on 2008-07-06
Brand new installation of Hardy won't recognise my wireless card, but Xubuntu does.  Both installed via "alternative" cd downloaded within the last two days.

Hardy:
```
ed@office:/# lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: wmaster0
       version: 00
       serial: 00:16:b6:5d:56:5e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
```
Xubuntu:
```
ed@office:/# lshw -C network
  *-network               
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: wmaster0
       version: 00
       serial: 00:16:b6:5d:56:5e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.101 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
ed@office:/# 
```
JUST WHAT IS GOING ON?  Same computer, different partitions.

Also, before these installations, I was running Hardy and was able to use a much higher screen resolution.  Both these installations default to 800x600 with nothing higher available.  Again same monitor as before and it did 1280 and 1024 resolutions.  Where should I go to get these recognised?  (and where should I go to get British spellchecking - this thing keeps red-lining recognise!)
```
*-display
             description: VGA compatible controller
             product: 82810 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810

```

Please help, as I can't get to synaptics on the ubuntu side to get my various bits for the new install.

---

