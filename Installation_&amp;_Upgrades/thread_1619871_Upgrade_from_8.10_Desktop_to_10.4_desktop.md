---
title: "Upgrade from 8.10 Desktop to 10.4 desktop"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by tdkryger on 2010-11-12
Hi

I'm considering upgrading my old fileserver from ubuntu 8.10 to 10.4, but i've got single concern, i'm hoping i can get some help with:
I have a 5TB sofware raid 5, that i realy don't want to loose in the process. And since it's almost full (below 1TB free), i can't do a full backup.

Is there any problem in with this, if i do the upgrade?
I guess i have to upgrade 8.10 to 9.4 to 9.10 to 10.04?

Best regards
Thomas

---

### Post by lemming465 on 2010-11-13
Assuming the the RAID is not mounted somewhere like /, /var or /usr you can either do the long upgrade via 9.4, 9.10, and 10.04, or perhaps just reinstall.  In either case, so long as you don't reformat the RAID, it should be preserved just fine.

---

### Post by tdkryger on 2010-11-16
It did indeed work

---

