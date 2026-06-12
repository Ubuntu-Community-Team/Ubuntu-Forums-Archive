---
title: "Can I fix broken apache2 install *just* by preserving /etc/apache2?"
date: 2014-11-18
forum: Installation &amp; Upgrades
---

### Post by bill.damage on 2014-11-18
Background is /var/cache has been totally deleted. I've made some progress fixing it but am now at the stage where if I try apt-get update it complains the apache2 package is not configured. Since I didn't touch /etc/apache2, I'm thinking if I preserve it with its 100+ domains, then totally uninstall and resinstall apache, then restore /etc/apache2, will I be good to go? Thanks.

Ubuntu 14.1

---

