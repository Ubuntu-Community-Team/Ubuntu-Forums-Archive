---
title: "I can't update after changes in PPA Graphic Drives repository"
date: 2018-10-27
forum: Installation &amp; Upgrades
---

### Post by juanramoncastan on 2018-10-27
After some changes made in "ppa:oibaf/graphics-drivers" repository give me the next warning message (spanish):

El repositorio «[http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) bionic InRelease» cambió su valor «Label» de «Updated Open Graphics Drivers» a «Updated Open Graphics Drivers - since 2011!»
N: Esto debe aceptarse explícitamente antes de que se puedan aplicar actualizaciones para este repositorio. Consulte la página de manual de apt-secure(8) para obtener más detalles.

There is some way to "Accept explicitly" this change?
Thanks in advance.

---

### Post by kc1di on 2018-10-27
I think the easiest way would be to remove that PPA  and run ```
sudo apt update && sudo apt upgrade
``` Then add the PPA again and try ```
sudo apt update 
```again. Good Luck.

---

