---
title: "lvpm failed (?) -- cannot boot"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by bmf1972 on 2007-09-13
I have Pentium III machine with two HDs, with an Win2K installation. The CDROMs are quite old and I couldn't boot Ubuntu since the ISO is a 700MB one :-(

I decided to go with Wubi... Installed Wubi, fixed a mouse problem (serial mouse wasn't recognized), created a VPN connection to my ISP and everything went OK but quite slow. I decided to use LVPM to transfer the Wubi partition contents to a dedicated partition.

On the empty space of my hd0 I created a new ext3 partition (forgot to create one for the swap...) and did a transfer using the last version of LVPM. Rebooted... and now I am getting the grub> prompt !!!

I tried to boot Ubuntu from the dedicated partition using root (hd0,2) and I am getting "Error 18: Selected cylinder exceeds maximum supported by BIOS" -- seems like I am stuck...

Any way out of this?

Please help,
Adrian.

---

