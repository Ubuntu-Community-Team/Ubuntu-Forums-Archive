---
title: "Uninstall Google Earth"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by Sachil on 2011-05-25
Hi,

I initially tried to install Google Earth an incorrect way, but have now managed to do so successfully through the repositories.  

However, I don't know how to undo 2 of my previous steps from my initial installation attempt.  They are:

1) sudo make-googleearth-package --force

2) sudo dpkg -i ./googleearth_5.1.3535.3218+0.5.7-1_i386.deb

Please help!

Thanks!!  :)

---

### Post by tommcd on 2011-05-26
Try running:
```
sudo dpkg -r googleearth
```
or 
```
sudo dpkg --purge googleearth
```
You may need to reinstall the googleearth from the Ubuntu repos after doing this; but this should not be a problem.

---

### Post by Sachil on 2011-05-27
Thank you!  You're a genius!!  :)

---

### Post by tommcd on 2011-05-28
> **Sachil said:**
> Thank you!  You're a genius!!  :)
Glad I could help.
Just out of curiosity, did you need to reinstall the googleearth from the Ubuntu repos after running the 
*dpkg* command?

---

