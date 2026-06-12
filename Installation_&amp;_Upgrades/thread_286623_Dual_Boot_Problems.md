---
title: "Dual Boot Problems"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by J.Pulumbarit on 2006-10-28
i recently had a perfectly fine running dual boot system with Ubuntu and XP. the xp partition got a virus so i decided i was goign to wipe the partition and just reinstall it. my setup had been 4 partitions, 1 xp and 3 ubuntu. after i booted with a xp install cd and deleted the xp partition i tried to format the new free space to NTFS but couldnt do so because it only allowed me to have 3 partitions on my hdd. so took a ubuntu setup cd and booted into that and formatted the free space into a NTFS partition. i was then able to install windows. the problem now is that when i turn on my comp it boots straight to windows with no grub. my old linux partitions which were seen from my computer are also not there anymore. i am 100% positive i only formatted the free space to NTFS. i kno however i had some utility that allowed windows to read ext3 so maybe thats why they are not showing up. i just want grub to appear back though mostly and be able to use ubuntu again.

---

### Post by Herman on 2006-10-28
That's an easy problem to fix, Windows has corrupted your MBR with its own bootloader code without even asking you for permission and it's way too dumb to add any other operating systems and boot them like Grub can.  :D

To fix your MBR so it is clean again and re-install Grub, just boot the Ubuntu Live CD and do something like this, 
                             Re-install Grub with a GRUB shell eg; with Live CD..........................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

You should try to select the most recent Ubuntu install from the list of partitions that contian a menu.lst filw (from the feedback from the 'find /boot/grub/menu/lst command in that link). If you don't get the right one the first time it won't matter too much though, just try again.

Regards, Herman :D

---

### Post by J.Pulumbarit on 2006-10-29
thanks for pointing me in the right direction, i fixed my problem

---

