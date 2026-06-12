---
title: "removed old partition and now new install doesn't boot"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by kelsonbaird on 2012-05-05
So long story, I had a dual boot system with win7 (sda1) and ubuntu 12.04 (sda5&swap sda6), and a shared NFTS partition(sda4). I didn't like unity and gnome was not working very nicely, so I ended up corrupting that system, I installed a clean version on 10.10 (and then upgraded that to 11.04) at the end of the hard drive in it's own new partition(sda 7 and sda 8.) Anyway it was working fine as a tri-boot system minus the fact that 12.04 wasn't booting, so after I got all the info I needed off 12.04 I wanted to delete it and it's swap drive and resize my new operating system. but once I deleted the old partition, my computer renamed the new 11.04 partitions as sda6 and sda7 and now the grub2 doesn't load at all. I am using the live disk to view things right now. Any Ideas how to fix this. I was thinking that maybe upgrade-grub  but that is not working from the live CD. and not sure if it would fix the issues anyway.

---

### Post by kelsonbaird on 2012-05-05
Ahhhh nevermind. Simple solution, just reinstall the grub2 file using chroot.

---

