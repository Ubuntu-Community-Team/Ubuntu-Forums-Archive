---
title: "Update Manager stopped worked (http error 127)"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by benali72 on 2011-01-12
Hi,

I have 10.04 installed and Update Manager has worked fine for months, until about 2 weeks ago.

When I ask Update Manager to update its indexes, I get this error message returned almost immediately --

"Method http has died unexpectedly!
Sub-process http returned an error code (127)
Method http has died unexpectedly!
Sub-process http returned an error code (127)

The internet connection is working fine on this machine.  

I have another 10.04 machine sitting right next to the problem computer, and Update Manager works fine on that machine.  I verified that all settings are the same between the 2 machines in these areas --

1. All Update Manager SETTINGS (including SOFTWARE SOURCES)
2. System -> Preferences -> NETWORK PROXY 
   (which is a Direct Internet Connection)
3. System -> Preferences -> NETWORK CONNECTION

It appears to me that the connection to Ubuntu repositories is failing but I can't find anything different between the 2 machines.

Any ideas? 

Thank you for your help!

---

### Post by dino99 on 2011-01-12
are your both pc connected the same way ? (proxy, router, switch, firewall, snort, squid, ...)

the logs might help you (xsession-errors, user.log, system.log, messages.log)

---

### Post by benali72 on 2011-01-12
Yes, both PCs are connected exactly the same. 

Thanks for listing the relevant logs.

I have inspected them and was unable to find anything relevant to my problem (tho I admit I'm not experienced reading the logs so even tho I was careful it's possible I missed something).

Anyone have other ideas?

I guess if I can't figure this out I will have to re-install Ubuntu. That's ok by me, but the trouble is... what if this problem re-occurs?  I have only installed programs from the allowable Repositories listed in Software Sources and haven't done any system tweaking to my knowledge, so I have to wonder if a re-install will enable me to avoid this re-occuring or not.

Thank you.

---

### Post by benali72 on 2011-01-15
No one has any other ideas on how to approach this problem?

I guess I'll do a recovery but I'll turn off Update Manager and not do any updates... I don't want this problem to re-occur.  Better an un-patched 10.04 than having Synaptic refuse to do any installs!

Thank you.

---

### Post by benali72 on 2011-01-17
Gave up. Did a recovery. Recovery was easy but it's disturbing that I never found the problem. Oh well here's to hoping it doesn't happen again.

---

