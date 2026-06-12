---
title: "Error trying to install regular updates to Hardy Heron"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by raj727 on 2008-09-13
I just got an error while trying to install one of the regular updates.  I haven't had this problem before.  When I went to install today's regular updates, I got the following error message:

E:dpkg was interrupted, yuu must manually run 'dpkg--configure-a' to correct the problem.
E:_cache->open()failed, please report.

Does anyone know how I would fix this?  Is there some command in Terminal that I would need to run?

---

### Post by Pumalite on 2008-09-13
sudo dpkg --configure -a

---

### Post by raj727 on 2008-09-13
Thank you.

That command also fixed my Google Earth 4.3 software which previously did not work.

---

