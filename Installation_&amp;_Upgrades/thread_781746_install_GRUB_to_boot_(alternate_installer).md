---
title: "install GRUB to /boot (alternate installer)"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by sorazer on 2008-05-04
I need to install GRUB to /boot instead of MBR. I tried the (K)Ubuntu alternate discs (I need encryption) in a VM and couldn't find a way to convince the installer... Is there a way to do that?

The reason is that my Windows partition is encrypted as well and GRUB jumping into the MBR breaks it. I could install green ol' Susie fine with GRUB going to /boot, I wonder if the Ubuntu installer can do this too?

---

### Post by jpyanowski on 2008-05-04
The answer is Yes! I use this method because I also have Vista on my laptop. The ubuntu install will let you select the partition to install GRUB in. You then use Easy BCD to select which OS to use. Good Luck

---

### Post by sorazer on 2008-05-04
What did I miss? Where exactly does it offer that option?

---

