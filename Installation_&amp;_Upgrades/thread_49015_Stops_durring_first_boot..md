---
title: "Stops durring first boot."
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by mem7 on 2005-07-14
After I'm done with the live CD and I'm doing my first boot it locks up at,
"Setting up xserver-xorg (6.8.2-10) ..."

Thanks in advance.

---

### Post by alastair on 2005-07-14
Graphics card? etc. ....

Can you switch to another terminal VT? CTRL+ALT+F1?

If so, what "Driver" in the X config file /etc/X11/xorg.conf

Try editing it (copy it to a backup first), and change to :

Driver    "vesa"

perhaps.

---

