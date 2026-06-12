---
title: "X Server fails on Installation"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by bluewagon on 2007-04-20
while trying to install any Ubuntu( ive tried 7.04 and 6.10) i get the error that the X server has faile.. it tells me
Fatal Server error: No screens found
under sudo nano /etc/X11/xorg.conf it has this

selection "screen"

    Identifier "Default Screen"

    Device "Intel Corp. 82845G / GE Chipset Integrated Graphics Device"

    Monitor "776"

    Default Depth 24

the onboard is disabled, ive tried enabli it to see if it would work but it doesnt, i currently have a NVIDIA GeFore FX 5500

and another thing, when trying to do
sudo dpkg-reconfigure -phigh -xserver-xorg
i get this error:

    Xserver-xorg postint warning: overwriting possibly-customised configuration file; back up in /etc/X11/xorg.conf.(then numbers)

also:
Pentium Celeron processor 2.6ghz
1 gig of ram
one 125 gig seagate hard drive(master with windows)
one 250 gig seagate hard drive (slave with nothing on it, new-just partitioned - putting ubuntu on it)
LCD Monitor1280x760

---

### Post by sharke on 2007-04-20
By what you have shown us x is trying to use onboard graphics.
Do the reconfigure for xserver  and ignore the warnings they are only fo info Make sure you select the correct graphics driver and set your monitor correctly.
Regards
Sharke

---

