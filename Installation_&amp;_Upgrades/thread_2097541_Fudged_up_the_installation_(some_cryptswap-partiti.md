---
title: "Fudged up the installation (some cryptswap-partition)"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by Askel on 2012-12-23
Hello

I was going to reinstall ubuntu without changing my home-partition. It didn't work out as planned. I used one partition for root (and formated it) one for boot (and formatet that one to) one for swap and one for home (wich i didn't format)
During the installation something happened when I was to choose username and password. The install got stuck. I rebooted and tried again. But it didn't work.over the sda was something called sda/mapper/cryptswap in the same size as my swapmemory. It could not be removed and I could not create the partitions. It starts but cancels cause it can't create a swap-partition.

While starting the computer grub doesn't load. It says:
 error: file not found.
Grub rescue> _

Please help me save my computer.

---

