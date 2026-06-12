---
title: "language-pack-bsb package broken"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Rock on 2008-06-09
i cannot upgrade anything in apt because this package is broken and when i try to fix it, it wont install because it says it will break other packages. it wont let me remove it either.

---

### Post by Rock on 2008-06-09
Problem solved, I did sudo dpkg -r --force-remove-reinstreq  language-pack-dsb and everything is fine now.

---

