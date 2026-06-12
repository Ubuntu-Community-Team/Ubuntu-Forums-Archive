---
title: "Problem (after) installing 12.04"
date: 2012-12-06
forum: Installation &amp; Upgrades
---

### Post by icyisaac100 on 2012-12-06
I have had problems after installing 12.04 on my desktop.  The GRUB menu automatically pops up when I load, and If I click the 'run normally' option it gives me  Busybox. I've tried many solutions on this forum, but none have really worked.  Any  clear visible specs wrong or not supported?

Specs
Intel Xeon(R) CPU L5420 @2.5GHz x 4
Graphics Unknown ? (what it says in settings ran from liveCD) 
4 Gig Ram
21.5G IDE hard drive IBM Deskstar (very old)
32-bit Ubuntu OS

Changing some things in BIOS/typing radeon.modeset=0 in the GRUB helped it load, but ran very slowly, and now the settings have been lost. LiveCD runs fine.

Graphics 
after typing sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:dc00(size=8)

---

