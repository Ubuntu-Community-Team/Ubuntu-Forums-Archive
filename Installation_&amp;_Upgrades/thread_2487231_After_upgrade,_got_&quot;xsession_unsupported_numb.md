---
title: "After upgrade, got &quot;xsession: unsupported number of arguments (4)&quot;"
date: 2023-05-28
forum: Installation &amp; Upgrades
---

### Post by janko-pbf on 2023-05-28
I upgraded from 22.04 to 23.04 and my session manager changed. I can't get ubuntu session manager anymore. When I try, I get an error: xsession: unsupported number of arguments (4):  falling back to default.

---

### Post by janko-pbf on 2023-05-28
It is fixed with ```
sudo dpkg-reconfigure gdm3
``` I got the standard ubuntu gnome session manager.

---

