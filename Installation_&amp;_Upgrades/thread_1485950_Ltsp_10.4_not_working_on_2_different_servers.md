---
title: "Ltsp 10.4 not working on 2 different servers"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by krobbe on 2010-05-17
I have a edubuntu 9.04 LTSP 32bit (on AMD Phenom II x4) with one TC -HP T5500 running. Fixed IP on the LAN. Std DHCP on the TC side.
For several reasons I like to upgrade 10.4 ltsp. 
Before doing this I have tested the edubuntu live LTSP on the above configuration. Everything works except the thin client gives the message PXE-E51 no DHCP offered... 
I have downloaded an other Image on an other machine with the same results.
Thereafter I have Installed edubuntu 10.4 LTSP 32 bit on an old AMD AMD Athlon +3200
Same results. I have been looking for solutions, have replaced a NIC, adopted the bug fix for the Network Manager etc.
Both NICs are recognized an have the expected IP (ifconfig readout) DHCP server is running. Restarted and started DHCP server
Following a treath I have done sudo chgrp dhcpd /etc/dhcp3/dhcpd.conf to ensure that the group is DHCP instead of ROOT. I have just found out that the DHCP3-server has changed from 3.1.1 to 3.1.3 in Ubuntu 10.4
I think that this must be a bug as I have the same problem on 2 different machines.

**After hours searching I have hooked up an laptop as TC and these was booting without a problem with edubuntu 10.4 LTSP.  **Should this be considdered as a bug?

---

