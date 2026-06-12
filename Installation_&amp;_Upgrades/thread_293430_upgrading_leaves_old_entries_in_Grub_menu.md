---
title: "upgrading leaves old entries in Grub menu"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by jnoreiko on 2006-11-05
I use grub to dual-boot with Windows.
Originally, my grub menu was:

Windows
Ubuntu kernel [version]
Ubuntu kernel [version] [some sort of safe mode]
memtest

Both times I've upgraded (to Dapper and now to Edgy), the old kernel versions remain in the menu, so I now have 6 Ubuntu boot items in all.

Is this a bug?
Is it safe to remove the old entries by hand from the grub menu file?

---

### Post by Kateikyoushi on 2006-11-05
Yes it is safe to remove them by hand if you do not use them anymore, check in synaptic whether the packages are still installed it usually removed the grub entries with the packages in my case.

---

### Post by jnoreiko on 2006-11-05
Yes, Synaptic shows linux-image-2.6.12-9-386 for example.

Is that safe to remove?
It doesn't have an Ubuntu logo in the 2nd column, though I've never quite worked out what that means anyway.

---

