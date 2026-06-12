---
title: "Can't get my modem to work"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by Ernest S Harris on 2005-03-15
I have installed Ubunto on my IDE2, with WindowsXP pro on IDE1. I am totally new to this operating system and have no idea what I am doing. I cannot get on the internet because my modem does not work. It shows as

Vendor: Rockwell International
Device: HCF 56k Data/Fax/Voice/Spkp(w/Handset)modem
Status: Status
Bus Type: PCI
Device: Unknown
Capabilities: Unknown

I have to keep rebooting into XP to be able to get onto the internet. What can I do to get the modem working?

Please assist  ](*,)

---

### Post by alastair on 2005-03-15
It's hard to say - remember that some modems (most maybe) are now "winmodems" i.e. the modem driver/software is where the "intelligence" lies, not in the modem itself. The problem is .... the software/driver is usually windows only. The best options are still the old external serial type i..e good old-fashioned USR sportsters etc.

Go here :

[www.linmodems.org](www.linmodems.org)

and have a read. There is a utility called "scanmodem" that you can download and run (in linux) - this helps identify what linux support you might need. The program is quite good - and includes lots of good information. See what it says about your modem.

---

### Post by az on 2005-03-15
"Vendor: Rockwell International
Device: HCF 56k Data/Fax/Voice/Spkp(w/Handset)modem"

That is a conexant modem.  The only driver available for linux is proprietairy and costs about the some as a new modem would cost you.  The driver they will sell you will work for a year.  When you upgrade your kernel, you may have to purchase the driver again.

They do not care about your freedom to use open source software.  

A modem with a better record is one based on the intel chipset or the lucent chipset.  Some intel chipset modems can be run on (mostly) GPL drivers while the Lucent ones are free, but proprietairy (no source code)

---

