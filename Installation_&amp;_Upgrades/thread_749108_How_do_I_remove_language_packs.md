---
title: "How do I remove language packs?"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by DrFixxer on 2008-04-08
Hi, 

My updates this morning seem to include a lot of Language packs, for languages I don't speak, nor know  anyone that might use my machine who does speak them. 

Is it possible for me to remove these language packs as I would assume they are just taking up space. 

Many thanks!

---

### Post by Cope57 on 2008-04-08
```
sudo dpkg-reconfigure locales
```
This should fix it.

---

