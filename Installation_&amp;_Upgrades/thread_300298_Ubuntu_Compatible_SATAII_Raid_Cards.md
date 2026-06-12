---
title: "Ubuntu Compatible SATAII Raid Cards"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by kc2aqg on 2006-11-15
Hi All-

This is my first post after doing a search and I'm looking to get some info on which SATAII PCI RAID Cards would be compatible with Ubuntu (I haven't decided on a specific version yet).  

Here is my basic hardware plan for setup:  Intel Celeron 2.2Ghz w/ standard Socket 478 Mobo (I have both so far), 512MB RAM

My goal for this is to set up a Samba server with a PCI Gigabit LAN card and a PCI SATAII RAID Card probably running RAID0 on two 500GB Seagate SATAII drives (brand new)

I can tell you that the Mobo doesn't have any PCI-E slots, just standard PCI so that's the type of card I'm looking for.  

My plan, as I have done in other Samba servers, is to install the Ubuntu OS to a Maxtor 80GB IDE drive running of the Mobo IDE controller.  I want to set up a 1TB RAID0 array between the two 500GB drives and use it as the Samba share space.  That's all the machine has to do is sit there and serve.

Also, budget is somewhat of a factor here.  I wasn't looking to spend too much on a raid card (> $150), but I do want hardware rather than software RAID.  So which cards should I look into with these criterion?  

And while we're at it, can anyone tell me which Gigabit NIC cards would also be compatible?

Thanks for any and all responses!

---

### Post by The Warlock on 2006-11-15
That Gigabit LAN card in itself just about saturates the PCI bus (max PCI bus speed: 1.03GBps total). Throwing a SATA card in there will definitely not help.

---

