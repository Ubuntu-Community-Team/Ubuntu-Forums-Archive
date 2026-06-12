---
title: "[resolved] Connecting a printer shared over ethernet"
date: 2004-12-20
forum: Installation &amp; Upgrades
---

### Post by 8oluf7 on 2004-12-20
I have three computers ethernetworked to share an ADSL modem (which also contains a router and firewall) and an HP Deskjet 6127 printer, which contains its own print server. One Windows XP, one Windows 98SE laptop (I can't switch these to linux yet - their users won't have it) and, my pride and joy, a brand-new home-built Athlon 64 SFF for running Linux. There is an ethernet switch, but this is not a client-server set-up. 

Respect to the guys who designed the Ubuntu install process. Everything appeared to go smoothly, and I was able to go straight onto the internet from the new machine and update the software. (By contrast, an attempt to install Fedora bombed because it couldn't recognise the SATA drive). 

But, although the network is obviously working (because I can access the internet), I can't get the new machine to talk to the printer. I've used Computer> System Configuration>Printing>New Printer to get to the set-up screen. Set printer type to network; Set CUPS Printer (IPP); Set URI: [http://xxx.xxx.x.xx](http://xxx.xxx.x.xx). Save and try to print a test page. I get a message 'Printer busy, retry in 10 seconds'.  No other machine is trying to print - and, anyway, the built-in print server is able to cope with up to four connections. 

I've tried removing and installing this printer several times, and the only variation is that CUPS sometimes crashes. 

What have I done/not done? It's driving me frantic!

---

### Post by 8oluf7 on 2004-12-21
> **8oluf7]I have three computers ethernetworked to share an ADSL modem (which also contains a router and firewall) and an HP Deskjet 6127 printer, which contains its own print server. One Windows XP, one Windows 98SE laptop (I can't switch these to linux yet - their users won't have it) and, my pride and joy, a brand-new home-built Athlon 64 SFF for running Linux. There is an ethernet switch, but this is not a client-server set-up. 

Respect to the guys who designed the Ubuntu install process. Everything appeared to go smoothly, and I was able to go straight onto the internet from the new machine and update the software. (By contrast, an attempt to install Fedora bombed because it couldn't recognise the SATA drive). 

But, although the network is obviously working (because I can access the internet), I can't get the new machine to talk to the printer. I've used Computer> System Configuration>Printing>New Printer to get to the set-up screen. Set printer type to network said:**
> http://xxx.xxx.x.xx[/url]. Save and try to print a test page. I get a message 'Printer busy, retry in 10 seconds'.  No other machine is trying to print - and, anyway, the built-in print server is able to cope with up to four connections. 

I've tried removing and installing this printer several times, and the only variation is that CUPS sometimes crashes. 

What have I done/not done? It's driving me frantic!
 Had another go after a good night's sleep. I had assumed that CUPS(IPP) was the correct option, because CUPS was used by other distros I tried. The correct selection is HP JetDirect.

---

