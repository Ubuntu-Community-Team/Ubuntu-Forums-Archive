---
title: "Server Hardware Upgrade"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by Dave.Wynne on 2010-11-17
My servers have 2 NICs and I use PCI cards rather than the motherboard on-board NICs, so that if I have a motherboard/processor/memory issue, I can buy a budget PC and put in the NICs and the hard drives, and press the start button and I'm back up and running.
BUT... new budget mother boards only have one PCI slot, so is there a way to add the NIC drivers after installation so I can change from PC to PC? Please note this will have to be a command line operation.

---

### Post by sikander3786 on 2010-11-17
> so is there a way to add the NIC drivers after installation so I can change from PC to PC? 

As far as those new NICs are supported in Linux, at every reboot, Kernel should detect new hardware and load the related modules/drivers for that device.

---

### Post by jpl888 on 2010-11-17
Yes and the only thing you will need to be mindful of is the way udev names and remembers network interfaces.

/etc/udev/rules.d/70-persistent-net.rules maps cards to interfaces names. When you change motherboard udev will create a new mapping probably to eth2 (as you already had 2 nics). In this case you should remove the entry for the old NIC (and the new one if you are doing this after moving motherboard).

I agree with you it's a good way to have things setup (I have been doing it that way for a number of years). If a server goes down just move the hard drive into another PC onsite and away you go. Makes more sense for companies that can afford an hour or 2 of downtime.

---

### Post by Dave.Wynne on 2010-11-17
> **jpl888 said:**
> Yes and the only thing you will need to be mindful of is the way udev names and remembers network interfaces.
 
/etc/udev/rules.d/70-persistent-net.rules maps cards to interfaces names. When you change motherboard udev will create a new mapping probably to eth2 (as you already had 2 nics). In this case you should remove the entry for the old NIC (and the new one if you are doing this after moving motherboard).
 
I agree with you it's a good way to have things setup (I have been doing it that way for a number of years). If a server goes down just move the hard drive into another PC onsite and away you go. Makes more sense for companies that can afford an hour or 2 of downtime.
 
Thank you very much I was unaware of *etc/udev/rules.d/70-persistent-net.rules*, this should get me out of trouble when I have to fix something.

---

