---
title: "Extra GRUB entries after update"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by Crazyap7 on 2011-04-26
I recently did a clean re-install with Ubuntu 10.10 to clear out all of the old experimentation that had gunked the system and start clean, and upon update an extra entry was created in GRUB:
ubuntu-2.6.35-28-generic

The original one being:
ubuntu-2.6.35-22-generic

From Googling I can see that most often people just edit the Grub menu and remove the old entry, but I haven't really seen an explanation as to why it's there.

Any help appreciated, thanks!

---

### Post by psusi on 2011-04-26
It is there because when the kernel is upgraded, the previous versions are kept in case there is a problem so you can choose to boot the older version and have a working system.  You don't edit the menu to get rid of it; you just uninstall the old kernel with apt or synaptic.  Search for linux-image in synaptic and remove the older versions ( but NOT the current one ).

---

### Post by Quackers on 2011-04-26
It's there as a fallback, in case the newer kernel doesn't boot, or fails in some way. Some users recommend keeping the last 2 kernels as a safety precaution.
If you want to remove the older one you can do so by entering its number in the search box of synaptic package manager then marking (all 3 parts) for complete removal and applying the change.
To update the grub menu afterwards you need to run sudo update-grub in the terminal.

---

### Post by Crazyap7 on 2011-04-26
Alright that clears it up, thanks!

---

