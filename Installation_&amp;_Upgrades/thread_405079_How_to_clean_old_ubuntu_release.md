---
title: "How to clean old ubuntu release?"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by HolyJoe on 2007-04-09
under /boot/ directory, there have some old img, and at / directory too.

how can i clean those old ubuntu release files security?

---

### Post by chewearn on 2007-04-09
You can uninstall the old kernel images using Synaptic.  Search for "linux", and unselect the appropriate entries (be extra careful though!):)

---

### Post by HolyJoe on 2007-04-09
thank you for you reply!

there is a another more security way to do it?

---

### Post by zvacet on 2007-04-09
```
cd /boot
```
and when you are in the boot directory
```
sudo rm -r file_name
```

---

