---
title: "Motherboard Upgrade"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by jmilk on 2007-01-24
A few months ago, I put together a new fileserver on a "spare" Athlon XP 2200+ board.  I popped in a 3ware 12-port sata, a ton of drives and a PCI-based gigabit ethernet card.

I think I was pretty smart in configuring the drives on LVM with one large /data partition under xfs -- this should be extendable when I run out of space and add more drives in a second raid-array.

However, I was completely DUMB when choosing the motherboard (choosing here means "prying it out of an obsolete compaq").  Due to the gigabit port sitting on the PCI bus and sharing bandwidth with the 3ware controller, network performance tops at less than the 100mbps speed I get on the integral ethernet port.

Well, I'm finally going to do something about this -- I found a nifty (inexpensive) motherboard with integral gigabit port (running on PCI-X), so the RAID controller gets the PCI bus all to itself.  

My question now is -- should I expect any problems (and if yes, what sort) when swapping the motherboard/processor in that machine?

Secondly, I'm currently running i686 -- what would it take to upgrade a running, configured system to AMD64?

---

