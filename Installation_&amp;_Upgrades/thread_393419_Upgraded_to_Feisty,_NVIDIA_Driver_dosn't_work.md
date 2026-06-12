---
title: "Upgraded to Feisty, NVIDIA Driver dosn't work?"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by tsav87 on 2007-03-25
Hey guys, I just upgraded to Feisty, but the nVidia driver that worked fine in Edgy doesn't work after the upgrade.  What do I do?

---

### Post by christhetechie on 2007-03-25
linux-restricted-modules has been held back. which contains a large chunk of the nvidia-glx driver.  

It WAS working yesterday.  I just did an apt-get update and fecked my system :P

For the minute, edit /etc/X11/xorg.conf and replace:

Driver "nvidia"

with 

Driver "nv"

---

### Post by tsav87 on 2007-03-25
darn, so I guess now I just need to wait for the update to fix it.

---

### Post by tsav87 on 2007-03-25
Is this part of the problem?

---

