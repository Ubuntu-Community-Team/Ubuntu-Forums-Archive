---
title: "Intrepid sighting"
date: 2008-05-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-05-26
OK--I'm here

---

### Post by spamzilla on 2008-05-26
I still have an issue with debconf, so I cannot upgrade, and I haven't had time to find a workaround atm. Hopefully soon I'll be using Ibex though :)

---

### Post by autocrosser on 2008-05-26
Will be glad to see you my friend!!

Luck!!

---

### Post by ejohney on 2008-05-26
> **spamzilla said:**
> I still have an issue with debconf, so I cannot upgrade, and I haven't had time to find a workaround atm. Hopefully soon I'll be using Ibex though :)

the debconf issue can be fixed by force installing findutils

sudo dpkg -i --force-all /var/cache/apt/archives/findutils_4.4.0-2ubuntu2_amd64.deb
or on 32 bit machines sudo dpkg -i --force-all /var/cache/apt/archives/findutils_4.4.0-2ubuntu2_i386.deb

then finish your upgrade as normal and debconf installs fine

---

