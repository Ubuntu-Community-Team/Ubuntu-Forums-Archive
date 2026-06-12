---
title: "network not working (realtek 8139 on shuttle zen st62K)"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by neoliv on 2006-06-04
Network (card) not working.

Get a NULL kernel pointer during boot: (dmesg partial hand copy follow)

eth0: RealTek RTL8139 at ...
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
8139cp: 10/100 Ethernet driver v1.2
Unable to handle kernel NULL pointer dereference at virtual address 00000004
printing eip:
c013e886 *pdc=0
Ooops 0002 [#1]
...
Call Trace:
irda_thread + 0xa3/0x00 [irda]
default_wake_function 

With pci=routeirq added to the boot options having similar proble.

kernel is the plain ubuntu 2.6.15-25 686 fresh from install.
Hardware is a plain ST62K with 512M a 250G seagate HD a P4 2.8G without added PCI-card.
 
Upgrade from 5.10 to 6.06 without a glitch (used the clean sources.lst)
Everything seems to work fine (video, sound, ...) but without network this box is not that useful (that's my HTPC + firewall/router/server)
Hope someone has a clue...
Thx for your help.

---

