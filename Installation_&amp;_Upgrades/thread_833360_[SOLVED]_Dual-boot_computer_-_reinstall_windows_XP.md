---
title: "[SOLVED] Dual-boot computer - reinstall windows XP safe"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by malaTG on 2008-06-18
Hi

I have a dualboot system because I still have some software that I want to use sometimes i.e. some games :)

My motherboard broke and I replaced it and everything on my ubuntusystem worked perfectly but my windows XP installation broke of course....

How do I reinstall my XP system so I don't break my ubuntusystem?

Thank you in advance

mala

---

### Post by housam on 2008-06-18
just prepare a ntfs partition to install XP  which will overwrite the MBR. then you will [[COLOR="Red"]_reinstall grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") to be able to boot both systems.

---

### Post by malaTG on 2008-06-21
Thank you for the help!

---

