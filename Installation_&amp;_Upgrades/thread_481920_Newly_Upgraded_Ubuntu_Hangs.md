---
title: "Newly Upgraded Ubuntu Hangs"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by delude on 2007-06-23
I upgraded 6.10 to 7.04 yesterday via the Update Manager. The system froze at 6min before completion. When I rebooted X wouldn't load. I did a "dpkg --configure -a", then "apt-get update" and "apt-get dist-upgrade" to make sure the upgrade was complete and rebooted. I managed to login to X but the system hung 3 min later while I wasn't doing anything. Now it keeps doing the same thing - runs for a few minutes that completely hangs (screen, mouse, keyboard).

Any suggestions on how I can repair this?

---

### Post by soul_rebel on 2007-06-23
perhaps try to boot with the old kernel and see if that happens as well.

---

