---
title: "full disk encryption on install"
date: 2019-01-19
forum: Installation &amp; Upgrades
---

### Post by ant2ne on 2019-01-19
nevermind, option does not exist on "live" iso.

---

### Post by TheFu on 2019-01-20
replied so this thread doesn't show up in "unanswered" list.

BTW, you can access dmcrypt /LUKs encrypted partitions and LVM LVs using live boot media.  Just boot from the flash ISO, get into the session, apt install lvm2 and cryptsetup stuff, then go to town doing the normal cyptsetup open, vgchange stuff.

---

