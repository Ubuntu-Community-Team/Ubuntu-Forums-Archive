---
title: "Setup up Ubuntu with Hybrid SSD (Dual Booting)"
date: 2012-11-24
forum: Installation &amp; Upgrades
---

### Post by dragnus on 2012-11-24
I have a Samsung series 7 Gamer laptop currently running Windows 7.

Specs are:

Screen Size 17.3 inches
Processor Type Intel Core i7 3610QM 
Processor Speed 2.3 GHz (Turbo boost upto 3.3GHz)
Memory RAM Size 16 GB
Computer Memory Type DDR3 SDRAM
Hard Drive 1 -  750 GB with 8GB SSD Hybrid
Hard Drive 2 -  750 GB
Graphics Card Description NVIDIA GeForce GT 675M
Graphics Card Ram Size 2 GB
USB 3.0

As you can see my primary hard drive has a 8GB SSD. What would be the best way to install ubuntu. Currently windows uses a program called ExpressCache using the SSD for the cache.

What would be the best option for dual-booting?
I was reading, and trying to see if there was a similar post. 

I don't fully understand the partitioning (root, swap, home) But I get the basics
From what I was able to understand, Swap space should be more than the RAM? But with 16gb of RAM, isn't that a lot?

Would the best set-up be installing Root onto the SSD, having 32gb (Double the RAM) as a swap on the Primary Hard-drive alongside windows and keeping home on the same drive. (I assume I would have to partition the 750gb hard drive with windows)

Also, if Ubuntu uses the SSD, windows would then be unable to use it correct? 

Thanks in advance
dragnus

---

### Post by mikewhatever on 2012-11-24
Can you boot from an Ubuntu CD/USB and post the ouptut of **sudo fdisk -l**. That will show how Ubuntu sees the hybrid hdd. There is probably no need for swap with so much RAM available.

---

