---
title: "Lucid upgrade wrecks Virtualbox"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by dianemeeks on 2010-05-10
I couldn't find anyone else with this problem, but now that I've solved it I thought I'd post my solution and maybe save someone else a couple of hours.
When I upgraded to Lucid, I had to recompile.  No problem, but afterwards vbox insisted it couldn't access the virtual hard disk although it had full permissions.  Eventually, I simply copied the .vdi to another location, gave it a new UUID, and removed the original.  Simple enough.

---

