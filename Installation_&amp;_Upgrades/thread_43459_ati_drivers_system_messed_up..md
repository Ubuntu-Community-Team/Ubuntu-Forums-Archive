---
title: "ati drivers/ system messed up."
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by graigsmith on 2005-06-22
i tried installing the ati drivers and i couldn't get it working.  so i just want to revert to the original drivers i had. and remove the ATI drivers.  how do i do this?

---

### Post by afonic on 2005-06-22
Just restore your xorg.conf file before the Ati installer changed it.

Even if you haven't kept a backup the Ati installer should have, search for it in /etc/X11

---

### Post by graigsmith on 2005-06-22
i fixed it.  restoring the xorg.conf file diddn't work.  whenever i did glxinfo in the terminal it would say direct rendering: No.   

i reinstalled xorg and anything it depended on.  and it started working again.

---

