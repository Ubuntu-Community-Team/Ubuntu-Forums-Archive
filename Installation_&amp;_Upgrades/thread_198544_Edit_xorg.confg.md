---
title: "Edit xorg.confg"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by foref0x on 2006-06-17
I tired to change HZ in the xorg.conf, but after reboot I can't enter X, how can I edit xorg.conf?

"gedit" -command dosent work?

---

### Post by briguy on 2006-06-17
use the nano editor.  You'll need to run as root:

sudo nano  /etc/X11/xorg.conf

crtl + O is save, ctrl + X is exit.

---

