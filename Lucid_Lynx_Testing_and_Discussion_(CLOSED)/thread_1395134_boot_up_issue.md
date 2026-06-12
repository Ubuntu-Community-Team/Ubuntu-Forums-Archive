---
title: "boot up issue"
date: 2010-01-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kouter on 2010-01-31
Upgraded to lucid from karmic, first boot went fine. Ran a prelink which froze, got an error something to do with bash and xmalloc, computer locked up so I rebooted.

Booting now, goes to grub, then to blank screen.  Booting into recovery mode, I get stuck..

hostname[249]: segfault at X ip X sp X error 4 in hostname
init: hostname main process (249) killed by SEGV signal
init: hwclock main process (250) terminated with status 2
sh: Out of space

followed by 4 more init...terminated with status 2

Fixable or do I need to reinstall?

---

### Post by Vanishing on 2010-01-31
> **kouter said:**
> Upgraded to lucid from karmic, first boot went fine. Ran a prelink which froze, got an error something to do with bash and xmalloc, computer locked up so I rebooted.

Booting now, goes to grub, then to blank screen.  Booting into recovery mode, I get stuck..

hostname[249]: segfault at X ip X sp X error 4 in hostname
init: hostname main process (249) killed by SEGV signal
init: hwclock main process (250) terminated with status 2
sh: Out of space

followed by 4 more init...terminated with status 2

Fixable or do I need to reinstall?

I figured every error in linux is fixable.

try to use the recovery boot option.
or chroot into your install, see if there's any boot up option you dont need.

---

