---
title: "chromium browser updation problem"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by varunsr11 on 2010-12-15
yesterday i have update chromium browser via update manager..just manual updation ..after chromium browser updation My ubuntu(10.4) crashed everytime when I close the chrome .

---

### Post by sikander3786 on 2010-12-15
You can try removing and re-install Chrome Browser. You might lose your bookmarks/settings that way.

Applications > Accessories > Termina:
```
sudo apt-get remove --purge chromium-browser
```

```
sudo apt-get install chromium-browser
```

---

### Post by varunsr11 on 2010-12-18
me update kernel .now its working fine

---

