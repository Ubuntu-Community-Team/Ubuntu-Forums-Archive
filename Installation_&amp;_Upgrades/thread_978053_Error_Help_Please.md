---
title: "Error Help Please"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by hatmancan on 2008-11-10
could someoine help me with this error message???
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081110193550
ty
help needed fast
hat

---

### Post by pennacook on 2008-11-10
> xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20081110193550

This is typical of any upgrade of xorg - but you might want to do a diff of the xorg.conf and the xorg.conf.200811100193500 to make sure that any special settings (adapter/monitor) are maintained with the upgrade. :)

---

### Post by hatmancan on 2008-11-10
pen
i have no idea what you just meant..
can you pls explain to me better
ty
hat

---

