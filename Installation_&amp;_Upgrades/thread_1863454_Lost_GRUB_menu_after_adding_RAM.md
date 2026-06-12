---
title: "Lost GRUB menu after adding RAM"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by ptmoy on 2011-10-17
I've been dual booting Ubuntu 10.04 desktop (64bit) with Window 7 (64 bit) on a Dell T110 PowerEdge Server (Server has 2GB RAM) since version 10.04 was first released.  Everything has been working fine.  Recently, I added memory by replacing my 2GB stick with two 4GB sticks for a total of 8GB.  After this, the GRUB menu for choosing which OS to boot no longer comes up.  Instead, the screen just flashes a few time, then computer boots into the default OS, which in my case is Ubuntu 10.04.  If I take out the new RAM and reinstall the original 2GB stick, everything works as before.  If I keep the 8GB in, and uninstall GRUB-PC and GRUB COMMON, I get the menu back but still can't boot into Windows 7, but I can still choose to boot into Ubuntu or Memtest without any problems.  If I re-install GRUB-PC and GRUB COMMON with the 8GB, original problem comes right back.

Does anyone know what's causing this behavior, and have any suggestion on how I can get GRUB to work with the added memory?

---

### Post by zvacet on 2011-10-18
Probably not a solution but doesn´t cost you anything.With your new ram boot in Ubuntu and run

```
sudo update-grub
```

and see if that help.

---

### Post by ptmoy on 2011-10-18
Thanks for your reply and suggestion.  That was actually one of the first thing I tried.  It didn't work.

---

