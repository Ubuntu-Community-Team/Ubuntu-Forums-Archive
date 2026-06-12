---
title: "Help Reinstalling packages off cd"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by benqbasic on 2005-09-08
Does anyone know how to reinstall most of the packages off the ubuntu cd.

I stuffed up in synaptic and removed all the packages that use sound :(


Thanks

---

### Post by swamytk on 2005-09-08
1. Edit /etc/apt/sources.list. Comment the all web site repositories except CD. usually first repository line in the file.
2. # apt-get update
3. # apt-get upgrade
4. # apt-get install *

---

