---
title: "USB devices missing"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by oscarBravo on 2008-03-22
I've got an interesting problem with a new install of Hardy, from the Alpha6 ISO (but continually updated since). One of my USB devices isn't accessible to me as my ordinary user, but is accessible to root. Specifically, it's a HP OfficeJet 4315 all-in-one printer/scanner/fax/coffee machine.

Strangely, I can print to it with no problems, but I can't scan from it. To scan I have to run xsane as root, which it complains bitterly about.

Even my lsusb output varies from normal user to root: ```
paul@vila:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
paul@vila:~$ sudo lsusb
[sudo] password for paul: 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 006 Device 002: ID 03f0:5411 Hewlett-Packard 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
paul@vila:~$ 
```

Any ideas?

---

