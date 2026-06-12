---
title: "HELP!  Ubuntu upgrade from 11.04 to 11.10 freezes"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by DBQ on 2012-01-15
Hi everybody.

Serious problem here.

When upgrading from 11.04 to 11.10, my terminal hangs on the line:

> 
"Setting up friendly-recovery (0.2.18) ..."


and after  >30 mins there is no progress. What do I do?  Am I pretty much screwed? Please help!

---

### Post by dino99 on 2012-01-16
seems that /etc/default/grub is not a genuine one, rename it. Be sure to only use grub2 (grub-pc), so grub-legacy/menu.lst have to be dropped first. That made, maybe a 
sudo grub-mkconfig
sudo update-grub

will do the job

---

