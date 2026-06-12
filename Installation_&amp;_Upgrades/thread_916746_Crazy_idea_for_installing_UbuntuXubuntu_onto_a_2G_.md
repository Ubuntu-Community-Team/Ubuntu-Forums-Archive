---
title: "Crazy idea for installing Ubuntu/Xubuntu onto a 2G EeePC"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by Carl H on 2008-09-11
How feasible is this?

I have an Asus EeePC 2G Surf, and a standard Ubuntu/Xubuntu install won't fit onto the internal disk. 

I've been wondering if I could do this:-

I install Ubuntu onto an SDHC card, and then remove a load of packages that I don't need, so that the total system fits onto the 2Gb SSD card. 

Then dd /if=/dev/sdhc/card of=/dev/ssd/card to copy the system to the SSD card, and tweak GRUB so it will boot from the SSD card. 

Will that work? Or am I missing something fundamental?

---

