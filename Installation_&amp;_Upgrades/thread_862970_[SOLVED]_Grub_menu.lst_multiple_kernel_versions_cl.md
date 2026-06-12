---
title: "[SOLVED] Grub menu.lst multiple kernel versions clutter or needed?"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by skunkbad on 2008-07-18
After a few kernel upgrades, the menu.lst becomes cluttered with a bunch of entries for old kernels. Can these safely be commented out or deleted? Is there any reason they would need to be held on to?

---

### Post by Oldsoldier2003 on 2008-07-18
> **skunkbad said:**
> After a few kernel upgrades, the menu.lst becomes cluttered with a bunch of entries for old kernels. Can these safely be commented out or deleted? Is there any reason they would need to be held on to?

Yes, you can safely remove old kernels. It's usually considered prudent to leave a backup kernel in case something happens.

The easy way to remove the extra kernels is to use Synaptic Package manager. Do a search for "linux-image" and mark your older kernels for complete removal. Synaptic will remove the kernels and clean up your grub menu.lst

---

