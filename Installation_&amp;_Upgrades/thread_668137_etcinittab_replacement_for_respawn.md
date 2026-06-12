---
title: "/etc/inittab replacement for respawn"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by jongt1 on 2008-01-15
Since ubuntu doesn't have /etc/inittab, where can I place respawn commands that used to be there? The reason for asking, is that I use qmail as my MTA, and this erquires a respawn command like (modulo typo and memory errors)

SV:123456:respawn /command/svscanboot

This isn't standard shell stuff, but presumably there's somewhere I can put it. Any suggestions?

---

### Post by tehet on 2008-01-15
Look at /etc/event.d/ But if you make /etc/inittab/ I believe it will be used as well.

---

### Post by jongt1 on 2008-01-16
Actually, inittab is ignored as far as I can tell, even if it's there. I found an alternative apporach, related to problems getting daemontools to work, which gets me a bit further, but not all the way. I intend to continue this discussion on that thread.

---

