---
title: "During install no partitions are found"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by Maupertus on 2010-04-10
Dear all,

I have the following problem installing Lucid Beta2.
When I come to the "Prepare Partitions" stage, the installer doesn't find any harddrives, even though Nautilus and Gparted do find them. 

What can I do to resolve this strange situation.

I'm trying to install ubuntu64

---

### Post by Maupertus on 2010-04-10
Okay, and for some reason NOW I find it after 2 hours of annoyed searching.
This worked for me.

Open Terminal and give
```
sudo apt-get remove dmraid
```

After this, no problems at all.

---

