---
title: "[SOLVED] multiboot and automatic upgrade from Feisty to Gutsy"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by RedPill on 2007-10-24
OK, last thread (at least from me!) on this topic.

If you use the automatic upgrade process to update one of your partitions from Feisty to Gutsy, ***make sure that the proper entries make it into grub's /boot/grub/menu.lst on your boot partition.***

In my case, the automatic upgrade process updated the /boot/menu.lst on the current partition, not my boot partition.

When I rebooted, I ended up selecting an outdated entry from the menu.lst on the boot partition, which caused all sort of headaches.  In particular, I could not get X to work with my nvidia 7300LE graphics card.

See related threads:

[http://ubuntuforums.org/showthread.php?t=590174]("http://ubuntuforums.org/showthread.php?t=590174")

and

[http://ubuntuforums.org/showthread.php?t=590117]("http://ubuntuforums.org/showthread.php?t=590117")

keywords: feisty gutsy upgrade problems 7.04 7.10 nvidia x multiboot multiple boot partition grub menu.lst


On the plus side, the new graphics are whizzy and fast :) - but so far, not worth the pain I had getting everything  working. :(

---

