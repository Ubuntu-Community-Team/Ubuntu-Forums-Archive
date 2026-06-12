---
title: "[SOLVED] Can 7.10 Upgrade to 8.04 Using Only CD?"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2008-07-05
If I go download 8.04 Media -- mine will be Kubuntu but this question could apply to all variants -- can I upgrade without using the network, as long as I check that the CD is to be used?

I know I have un-checked that the CD/DVD drive is to be used if I want network-only installations for applications, libraries, and so on, that I want to add after an upgrade or full installation. 

If I check the CD drive as a source of updates and put in what will now be the 8.04.1 media, will that upgrade from the new media, or still use the network first?

tnx

---

### Post by scragar on 2008-07-05
if the CD has the structure of a repository(so it's either an install CD or a CD made using something like aptOnCD) then synaptic will automaticaly see the CD and offer to use it as a local package storage, UNLESS the packages it has are older than the ones online(if that makes sense).

as for upgrading from 1 version to another(7.10 to 8.04) you can only do this using the alternate CD, and some programs will still have to download their updates once the upgrade is complete, but yes, it is possible.

---

### Post by avtolle on 2008-07-05
Not 100% sure I understand the question, but IIRC, to do an upgrade such as you are posting, one must use the alternate install CD for the upgrade.

---

### Post by TheSandman on 2008-07-05
Just tried this myself. Only from 7.04 and as you say for some reason only the alternate CD will even try to do this. The desktop Live won't.

Of course, didn't help since the tool apparently didn't support upgrade from 7.04

---

### Post by avtolle on 2008-07-05
From 7.04, either one needs to do a clean install from an 8.04 CD, or an incremental network install, totally updating 7.04, going to 7.10, totally updating 7.10, then go to 8.04. You may read about the "recommended" way at [www.ubuntu.com](www.ubuntu.com), click on upgrade, then read the appropriate link.

---

### Post by TheSandman on 2008-07-05
I'll try to 7.10 then 8.04 then.

The only reason for the 7.04 to 8.04 upgrade is that we tried to do a clean install from both 8.04 discs on a Lenovo notebook.
But for some reason the screen just goes black and freezes even in text based install with acpi off, won't even give me an error.
The 7.04 install disc worked well though... :confused:

---

### Post by avtolle on 2008-07-05
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) is provided just in case the sequential upgrade method puts you in the same position. Good luck; maybe the link won't be necessary.

---

### Post by TheSandman on 2008-07-05
Thanks!

Don't know which boot options to try that we haven't already though.
But if 7.04-7.10-8.04 doesn't work i'll give a clean 8.04 install another go.

---

### Post by cmnorton on 2008-07-08
> **scragar said:**
> if the CD has the structure of a repository(so it's either an install CD or a CD made using something like aptOnCD) then synaptic will automaticaly see the CD and offer to use it as a local package storage, UNLESS the packages it has are older than the ones online(if that makes sense).

as for upgrading from 1 version to another(7.10 to 8.04) you can only do this using the alternate CD, and some programs will still have to download their updates once the upgrade is complete, but yes, it is possible.

I've made the two alternate install CDs, one for Kubuntu and Ubuntu (both 7.10) respectively, and I'll give the update another run. The last time I updated, the update itself came back at the end and said it had failed. I had an original Ubuntu install 7.10 running the KDE desktop. This update will be purely a Kubuntu update.

---

