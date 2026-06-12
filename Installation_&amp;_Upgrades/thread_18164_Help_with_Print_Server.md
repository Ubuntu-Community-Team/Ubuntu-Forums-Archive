---
title: "Help with Print Server"
date: 2005-03-05
forum: Installation &amp; Upgrades
---

### Post by athem on 2005-03-05
I have an older Hawking Technologies PNP7127P parallel port print server attached to my linksys router.  It is given un ip address of 192.168.1.101, and responds to ping.

I've tried using the Gnome Printer Manager to configure printing using both cups and lpd, to no avail.  The settings for the print server are:

01 BoxName      : 1P_PrintServ802735
02 BoxVersion   : 5.51 (fixed)
03 BoxNodeID    : 00-40-01-80-27-35 (fixed)
04 DHCP/BOOTP   : ON
05 BoxIPAddress : 192.168.1.101
06 Gateway      : 192.168.1.1
07 SubnetMask   : 255.255.255.0
08 NetWare      : Disable
09 PrinterMode  : Fast (Fast, Normal, Slow)
09 Printer1Name : lp1 (fixed)

I've tried cups:

ipp://192.168.1.101/lp1

and lpd:

Host: 192.168.1.101
Queue: lp1

but can't get it to print  :cry: .  Any suggestions?

Thanks!

---

