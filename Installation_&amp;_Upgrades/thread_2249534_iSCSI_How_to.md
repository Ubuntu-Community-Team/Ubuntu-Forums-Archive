---
title: "iSCSI How to?"
date: 2014-10-22
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2014-10-22
It is the first time to work with such a machine and I am completely out of ideas ;-)

We got a used server with hot swapable harddisks. We actually do not need that, but it is there!
It is an IBM x3850, m2, 2x QC, Xeon E7420, 16 GB RAM
Unfortunately I try to help somebody remote to install with him, ... I am not at the machine!

We tried:
Server CD 14.04 und come to the point that it needs the hard disk. We used iSCSI and get:
enter an ip address to scan for ISCSI targets. To use a port other than the default of 3260, use "IP:port" notation, for example "1.2.3.4:3261

Looking up the LAN, and the notebook (192.168.2.103) beside, we choose an IP 192.168.2.10    ... did not work (No ISCSI targets discovered).

It seems we have to SET that, but where and how? We bootet from the server CD.



Next try was to take out the harddisks and plug in an USB drive, expecting that we can install the system onto the USB drive, but we come to the same menu to select a driver for the hard disk, that starts with iSCSI again. 


Either way would be fine. This server has simple task only work with data on multiple USB drives, therefore a USB harddisk installation would be fine too.

---

