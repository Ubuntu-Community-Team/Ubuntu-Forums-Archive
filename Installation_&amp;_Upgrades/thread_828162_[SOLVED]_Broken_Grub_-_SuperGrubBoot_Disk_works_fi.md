---
title: "[SOLVED] Broken Grub - SuperGrubBoot Disk works fine"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by NEUR0M4NCER on 2008-06-13
Hi all. I've done 'something' to my Grub whilst trying to re-install XP for dual-booting. Grub says 'Invalid device requested', so I tried changing /boot/grub/menu.lst root (hd0,1) to (hd0,2) through (hd0,5), but no luck. Funny thing is, [Super Grub Disk](http://www.supergrubdisk.org/index.php) can boot XP just fine...

So i'd like to know how to mirror the way SGD boots XP in my own Grub, get a working dual-boot back. Perhaps I just need to know the right device address?

Regards

---

### Post by NEUR0M4NCER on 2008-06-13
Never mind - I was being stupid. When I said i'd tried the other drive numbers... well, the only one I hadn't tried was (hd0,0). And that's what it was.

Sorry :)

---

