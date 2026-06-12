---
title: "Upgrading to 8.10 /var/cache free space error!"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Presi on 2008-10-30
I'm upgrading from 8.04 to 8.10. The installation fails cause it says /var/cache needs more free space. Even if the partition has 1.6 gbytes available, I've notice that the /var/cache folder has only 500 mb!? Only that folder gives me a wrong amount of free space.

Thanks

---

### Post by Presi on 2008-10-30
Anyone have an idea?

---

### Post by byxkbyxk on 2008-10-30
&#31995;&#32479;&#26377;&#39044;&#30041;&#31354;&#38388;

---

### Post by Presi on 2008-10-31
I speak italian and english

---

### Post by Partyboi2 on 2008-10-31
open a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get autoclean
sudo apt-get clean
``` This should make some space.

---

