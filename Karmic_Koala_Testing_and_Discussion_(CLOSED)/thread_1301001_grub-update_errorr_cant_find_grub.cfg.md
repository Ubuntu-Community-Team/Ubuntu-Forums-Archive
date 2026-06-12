---
title: "grub-update errorr cant find grub.cfg"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mick222 on 2009-10-25
Whats wrong here i edited grub.d/05_debian_theme to try to get a splash image when i run update-grub i get the following message. Seems i can boot mormally but grub won't update.

> -desktop:~$ sudo update-grub2 
Generating grub.cfg ...
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.

---

### Post by mick222 on 2009-10-25
ok fixed it had changed a line in /etc/grub.d/05_debian_theme by mistake

---

