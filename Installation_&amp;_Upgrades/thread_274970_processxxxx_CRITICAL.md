---
title: "process:xxxx: CRITICAL"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by coolclassic on 2006-10-10
This is an error which i am getting after upgrading to kde 3.5.4. The upgrade using adept seemed to go well, with adept showing upgrade completed. Next when restarting adept it protested that another process was being used. I then attempted to clear problem using "dpkg --configure -a" and got the following message for a number of programs:

** (process:9090): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

Can this be safely ignored and what does it mean?

---

