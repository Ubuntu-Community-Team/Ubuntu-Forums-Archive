---
title: "All sorts of grub2 problems after failed upgrade"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by DarthCrap on 2010-12-30
Hi

At the end of upgrading from 9.10 -> 10.04 (a few minutes after a successful upgrade from 9.04 -> 9.10), I got an error message that libatlas3gf-3dnow failed to install, and the upgrade aborted.

Since then, I've had quite a few problems. Ubuntu would boot, and upon reaching the logon screen, the screen would go half-black, and I could no longer use the keyboard/mouse to control.
I have since realised this is because GRUB2 was booting the wrong kernel, and after a lot of frustration, have managed to correctly run update-grub from a live CD.

I now have two further problems:
[LIST]
[*]When selecting Ubuntu from GRUB2, the screen goes completely black for two minutes before the purple 'Ubuntu Loading' screen is displayed. Half of the time, this loading screen then turns completely white with purple specks.
[*]My Windows XP Partition is detected, but is listed by GRUB2 as a recovery partition, and my actual recovery partition is not detected at all.
[/LIST] 

Is there any way of fixing these problems?

Thanks

DarthCrap

---

