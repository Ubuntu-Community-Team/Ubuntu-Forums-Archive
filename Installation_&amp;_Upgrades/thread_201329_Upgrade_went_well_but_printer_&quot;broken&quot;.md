---
title: "Upgrade went well but printer &quot;broken&quot;"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by jfl on 2006-06-21
Upgraded yesterday from Breezy to Dapper; no problems, a bit long, andI had to run "sudo apt-get dist-upgrade" 3 times. When I rebooted, I was a bit nervous, but bingo, here was Dapper =D> =D> =D> .

**Problem ONE**: My printer, HP laserjet 1200 is connected to a W2000 box on a Windows network. That worked fine with Breezy.
I tried to "add" the printer first as "CUPS" then as a windows printer ( I just couldn't remeber what I had done on Breezy); everything looks good, but the jobs stay in the local queue and never print. I installed the recommended driver "pxlmono".
The network connection seems OK, I can transfer files from the W2000 machine to and from the Ubuntu box.

**Problem TWO:**Since I really need to print (office environment), I connected the fax machine HP Officejet 4215 (All in one) thru a direct USB connection. No luck. 
I just need to print, I don't need to scan, fax or whatever...

Three months into Ybuntu, the learning curve is steep ](*,) 

Thanks in advance ...

---

### Post by chunk on 2006-07-20
I have the same problem (#2) with my Epson CX4200 printer (connected via USB) after I dist-upgraded from breezy to dapper.

Looks like ubuntu suffers from the old debian "apt-get is wonderful, but dist-upgrade will bork your system" problem.

Time to download the dapper install cd...

---

### Post by jfl on 2006-07-20
> **chunk said:**
> I have the same problem (#2) with my Epson CX4200 printer (connected via USB) after I dist-upgraded from breezy to dapper.

Looks like ubuntu suffers from the old debian "apt-get is wonderful, but dist-upgrade will bork your system" problem.

Time to download the dapper install cd...

You are right; I spent more time trying to make the "dist-upgrade" to work - with little succes than to do a full re-install - NOT from the LIVE CD, but the other one !

RE: Printer.
Did you try to download the latest driver from the Epsom web-site; it worked well for me, after I overcame the shock of seeing they actually had a driver and specific instructions for Ubuntu !!! At least for the LaserJet 1200.

Good luck !!!

---

