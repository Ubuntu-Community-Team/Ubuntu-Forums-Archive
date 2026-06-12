---
title: "Recent Upgraded Packages - Internet not working"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by staverts on 2007-02-14
Hello all, a recent updates showed up in my ubuntu/synaptec upgrade manager, it said there were 12 new updates.  I looked at the packages, they were all Ubuntu approved packages, with the xxubuntuxx.dpkg...I installed the packages upon review...and now my eth0 and eth1 card works intermitadly...something is effecting thier performance. 

Yes, I made sure it was not my internet connexction, I work as an Information systems tech for a school division, and tested several other computers on our network, thier internet speed is fine.

I checked my ip address, all looks good, I checked my DNS and gateway, all is good thier as well.  I did some pings, and it is taking WAY to long to get a feed in and out...my co-worker beside me did the same updates to his ubuntu, and is having the same problem as me....

Let me know if anyone has found a fix for this, or is having the same problem.

---

### Post by Leenie on 2007-02-19
I have the same problem.

After setting up 6.10 on a new system and downloading the updates for it, the internet performance went WAY WAY down, basically to the point of not having a connection.

I can ping locations on the internet and LAN, but I can not connect via http, ftp, etc. I can not run synaptic, my IP enabled desklets don't work, etc...

Here is my info if it helps anybody.  I tried the integrated NIC on the ABit KD7A motherboard and after it stopped working, I plugged in a 3Com 3C905c PCI card. Same problems.


--------------------------------------------
leenie@desktop:~$ sudo mii-diag eth1
Basic registers of MII PHY #24:  1000 782d 0040 6176 05e1 45e1 0003 0000.
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner advertised 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.




leenie@jim-desktop:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes
-----------------------------------------

This system has Ubuntu on SCSI and WinXP on IDE.  WinXP has no communication issues and Unbuntu did not - until I updated the system...

---

