---
title: "No shutdown following Xorg updates"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by Zill on 2006-08-23
New(ish) installation of Dapper on an old desktop PC.  Updated to the broken Xorg package (10.3) but then realised this before rebooting.  Then updated Xorg to 10.4 as advised.  Rebooting now seems to work normally and the PC (and X) works fine.

However, I cannot now shutdown the PC from the desktop - everything shuts down as normal and the HDD is unmounted but the PC remains powered-up showing the last message "Will now halt".

I have tried adding "acpi=force lapic" to the kernel line in /boot/grub/menu.lst and rebooting but this makes no difference.

I believe shutdown did work correctly before the Xorg hassle.  Shutdown also worked fine with the previous istallation of Mandriva.

Any ideas?

Many thanks.

---

