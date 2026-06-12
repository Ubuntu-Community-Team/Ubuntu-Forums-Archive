---
title: "[SOLVED] Grub - What happened?"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by JohnnyTricksta on 2008-09-11
ok, so I was dual booting with Ubuntu and Vista. I hated Vista so I got XP and I deleted Vista's partition and installed XP. Needless to say, it also deleted grub. After hours of FINALLY getting grub back, I now have a new problem. Grub seems to be pointing to the wrong partition. Whenever I select a partion, I get this error:

root (hd0,2)
Filesystem type unknown partition type 0x82

Error 17: cannot mount selected partition.

It's pretty much the same error when I select the Window's option.

However, I did figure out that I can push "e" to edit the command for booting. If I choose the Ubuntu partition, push e, then change (hd0,2) to (hd0,1) then Ubuntu boots just find.

My question is:
1) How can I permanently change the partition on grub to (hd0,1) so I don't have to change it each time I boot

2) How do I figure out Window's partition number so I can also change it


Thanks!

---

### Post by JohnnyTricksta on 2008-09-12
Ok, I fixed it :-D

I edited my GRUB file to reflect the partition, then found out that XP was (hd0,3) :) Everything is fixed now!

---

