---
title: "Upgrade icon problem"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by ronswift on 2006-10-09
While upgrading from breezy to drapper, I kept getting an error message that 'best' icon was not found. After completing the upgrade, whenever I start the system, I get the same error, Could not load icon; Details icon 'best' not found, after the desktop loads or when trying to change themes. 
Where can I find the 'best' icon?

---

### Post by dannyboy79 on 2006-10-10
i would suggest that you use a .iso explorer program and search the ubuntu live cd for the 'best' icon. that would be my best guess in trying to help you. i think there may also be a way to 'mount' an iso in linux if you don't have a windows box. just gogle it.

---

### Post by ronswift on 2006-10-10
Thanks, I found the best.png icon on another system using breezy ubuntu. It was in the /usr/share/gnome-app-install/icons directory. I copied it to my dapper system in the same directory and the problem persists. Any idea of where the icon should be stored to prevent the error messgaes?

---

### Post by ronswift on 2006-10-10
I put the icon in the /usr/share/pixmaps directory on Dapper and that solved the problem. Thanks for the help.

---

