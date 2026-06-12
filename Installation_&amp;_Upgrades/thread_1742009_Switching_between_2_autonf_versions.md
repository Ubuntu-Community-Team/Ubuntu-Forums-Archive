---
title: "Switching between 2 autonf versions"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by neoragexxx on 2011-04-28
I need to use autoconf 2.13 and i was wondering if i can install it on the side of my current version and if yes how can i switch between them afterwards ? 

thanks in advance

---

### Post by neoragexxx on 2011-04-28
i discovered it is possible to do just by sudo apt-get install autoconf2.13
but before doing that i renamed autoconf in /usr/bin/ to autoconf-2.65. 

that way i can move back and for with 
sudo ln -sf autoconf2.xx autoconf

---

