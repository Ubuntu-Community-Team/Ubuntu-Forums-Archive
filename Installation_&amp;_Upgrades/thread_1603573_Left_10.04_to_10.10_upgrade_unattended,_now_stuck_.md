---
title: "Left 10.04 to 10.10 upgrade unattended, now stuck on grub configuration"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by jonthysell on 2010-10-22
So I set my desktop to upgrade from 10.04 to 10.10 then left for work.

When I got home, the upgrade stopped with the window to configure grub.

The only problem is, it's behind the upgrade manager window, all of the window decorations are gone, and I can't select it, and the keyboard won't work.

I can open new programs, but they're undecorated and I can't interact with them either. I can switch to a console terminal, but have no idea what to kill/start to get moving again.

Help? Is it safe to reboot and then resume with a normal apt-get upgrade?

P.S. It might be something with having hit the screensaver and trying to lock while I was gone.

---

### Post by jonthysell on 2010-10-23
Rebooted, but different kernels meant different hangs in the boot process. Eventually got the recovery mode to work (took about an hour to get past a ureadahead-other error) but eventually I was able to get to the package repair, and voila, I'm on 10.10.

---

