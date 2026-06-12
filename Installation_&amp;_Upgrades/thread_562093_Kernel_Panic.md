---
title: "Kernel Panic"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by dgtldaydrmr on 2007-09-28
> Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

this occurred after the install of mac80211 and recompiling the Kernel

I don't really want an outright answer on how to fix it.

I would like to know what happened and why.


If someone could point me in the right direction it would be greatly appreciated.

Thanks in advance!

---

### Post by markoz on 2007-09-28
Hi,
It seam to me that # groot=(hd8,1) line in /boot/grub/menu.lst points to the wrong root partition. It is a little bit difficult to tell how it can happen. It happened to me too on some kernel upgrades.

Cheers,

---

### Post by dgtldaydrmr on 2007-09-28
working on that now.
:)

---

### Post by dgtldaydrmr on 2007-09-28
well I booted up with a knoppix CD and the lilo.conf seems in order ( I use lilo not grub on this HDD) 
not sure what happened or where the issue is.

For future use I'll be sure to make sure I can boot into my old Kernel when doing recompiling...Live a little learn a little.

---

