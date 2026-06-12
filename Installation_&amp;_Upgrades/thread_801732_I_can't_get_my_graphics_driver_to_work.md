---
title: "I can't get my graphics driver to work"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by Simscape on 2008-05-20
I have a NVIDIA GeForce 6200 on Ununtu 8.04, and the graphics driver is in restricted drivers, it's enabled but it says its not in use.
I can't change any visual effects or anything.
How do I fix this?
(I'd rather use this driver than try to install the one on nvidia.com, for some reason it can't open it, and I don't feal like getting into tons of things on here)

---

### Post by iaculallad on 2008-05-20
On the terminal:

sudo gedit /etc/default/linux-restricted-modules-common

and set this entry:

DISABLED_MODULES="nvidia nvidia_legacy"

Restart then try re-enabling restricted driver.

---

