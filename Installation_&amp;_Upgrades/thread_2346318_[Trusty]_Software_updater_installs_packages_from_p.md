---
title: "[Trusty] Software updater installs packages from proposed updates?"
date: 2016-12-13
forum: Installation &amp; Upgrades
---

### Post by cogset on 2016-12-13
I've noticed that some updates from trusty-proposed were installed in ubuntu trusty a couple of days ago by the update manager, this one [http://packages.ubuntu.com/trusty-updates/systemd](http://packages.ubuntu.com/trusty-updates/systemd) and some other related packages.

The changelog says ```
systemd (204-5ubuntu20.20) trusty-proposed; urgency=medium
```
 but I'm positive I don't have **trusty-proposed** in my sources neither I've checked proposed updates in the software manager: am I missing something here? 

Why am I getting software from proposed updates ?

---

### Post by deadflowr on 2016-12-13
The proposed in the changelog means the package was originally uploaded there. persumably for further testing.
That was on Nov 10.
It has since been adequately tested and approved, so they moved it to trusty-updates.

---

