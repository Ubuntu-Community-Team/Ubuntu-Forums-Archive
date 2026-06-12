---
title: "parallel ata mode Super!grub option"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by fumblefingers on 2011-07-12
This probably straddles too many areas to fit under any of the prefixes, nor neatly into any
forum, prolly, so don't all pile on spanking me.

I'm running Kubuntu 11.04 on an Intel 850 Pro mobo from early in the millennium.
To my surprise and appallment, the bios seems not to support "seeing" boot
info on a partition that begins past the 1024 cylinder boundary, even though the
bios dates from 2001.  Word on the street was that that problem vanished in
bioses hatched after 2000.

Super Grub Disk2 can boot to the problem partition, after I enable its parallel ata mode (I hope I remembered that right.)  No problem at all booting to that past 23GB mark partition (which is
another Linux.)

Anyone know if there's a means of giving the grub v.2 that Kubuntu runs that same capability?
It offends me not to be able to boot from the hd.

             --  ff

---

