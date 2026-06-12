---
title: "LiveUSB cannot boot on gigabyte motherhoard"
date: 2018-11-08
forum: Installation &amp; Upgrades
---

### Post by playeve on 2018-11-08
Hello, downloaded recent LTS Ubuntu and created a live USB by using Universal-USB-Installer-1.9.8.3

Trying to install it on GA-945GCM-S2C motherboard with E2220 CPU, but no go. After selecting USB-HDD as bootable device i got stuck on a screen with Tables "Listing PCI Devices", above that tables i can see that system detected USB drive too. 
I checked BIOS settings and enabled/Disabled everything related to the matter. As a side note: i dont have "quick boot" option, nor UEFI as those are common blockers. 

What I've tested so far:
1. This particular Ubuntu USB on other PCs  = **[COLOR=#008000]works [/COLOR]**
2. Windows USB on this PC = **[COLOR=#008000]works [/COLOR]**
3. PCIe USB expansion card to plug in USB there = **[COLOR=#ff0000]not working[/COLOR]**
4. Use live USB on all USB ports, including front panel = **[COLOR=#ff0000]not working[/COLOR]**
5. Install Windows XP to see if everything operational = **[COLOR=#008000]works[/COLOR]**

I've read somewhere about problems, when ubuntu block usb driver or something, but ran out of ideas how to install OS on that machine. 
Any ideas? 

P.s. no, i don't have DVD drive to read or write disks.

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

The configuration is pretty old.

[https://ark.intel.com/products/32430/Intel-Pentium-Processor-E2220-1M-Cache-2-40-GHz-800-MHz-FSB-](https://ark.intel.com/products/32430/Intel-Pentium-Processor-E2220-1M-Cache-2-40-GHz-800-MHz-FSB-)

[URL="https://www.gigabyte.com/Motherboard/GA-945GCM-S2C-rev-10#sp"]https://www.gigabyte.com/Motherboard/GA-945GCM-S2C-rev-10#sp 
[/URL]
I will suggest to use alternate image to boot the system and XFCE or LXDE Desktop environment during the installation.

Regards,
Mitesh

---

### Post by playeve on 2018-11-10
Solved. 
Installed ubuntu on other PC and simply plugged in that HDD to problematic machine.

---

