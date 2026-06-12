---
title: "files list file for package `evolution-webcal' is missing final newline"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by blightc on 2007-07-01
trying to apply the latest patches and I get this message:

files list file for package `evolution-webcal' is missing final newline

both by clicking the update icon and by running apt-get

completely cleared the cache with the same result

where am I being stupid ?

---

### Post by kaotikzen on 2007-10-23
give this a try:

sudo vi /var/lib/dpkg/info/evolution-webcal.list

write the changes vi made when opening the file (:w) and quit (:q)

---

