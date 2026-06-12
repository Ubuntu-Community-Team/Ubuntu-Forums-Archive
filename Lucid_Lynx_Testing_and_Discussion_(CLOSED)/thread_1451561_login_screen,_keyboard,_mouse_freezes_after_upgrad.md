---
title: "login screen, keyboard, mouse freezes after upgrade to 10.04"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Tomy on 2010-04-10
graphics = ATI HD 3200 IGP

After upgrading from karmic (with fglrx installed) to lucid my login screen is frozen solid forcing a power-down.

From recovery mode a have run "apt-get purge fglrx*" and deleted xorg.conf but login still freezes.

From recovery mode when I run "failsavex"  the screen still freezes solid with this error message:
> Ubuntu is running in low graphics mode
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.I copied xorg.conf.failsave to xorg.conf and changed Device from "fbdev" to "vesa". Now I get this error and everything still freezes solid.
> Ubuntu is running in low graphics mode
The following error was encountered. You may need to update your configuration to solve this.
(EE) VESA: Kernel modesetting driver in use, refusing to load
(EE) No devices detectedI just now (Sat April 10 around noon) upgraded again and picked up a new  ati radeon driver and changed xorg.conf Device to "ati" and the screen still freezes solid.

How do I can get my keyboard and mouse back? Seems I should reinstall something.

---

### Post by Tomy on 2010-04-10
bump

not having much success here. any ideas?


Update: I gave up and restored from backup.

---

