---
title: "Samba needs Glade on Lubuntu 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by SteveDee on 2011-05-01
After upgrading my media computer earlier today, I tried to run Samba config (system-config-samba) and it crashed.

Running again in terminal I got the following error:-
```

import mainWindow
File "/usr/share/system-config-samba/mainWindow.py", line 30, in <module> import gtk.glade
ImportError: No module named glade

```
Ths was fixed by installing (via Synaptic):-
```

python-glade2

```

---

### Post by ninti on 2011-06-04
Thank you for the post. Whenever I tried to access Applications - System - Samba it just wouldn't work. After I put in the password, it would just go right back to the desktop. Installing python-glade2 fixed my problem.

---

### Post by Amorget on 2011-07-17
Thank you!  Same problem, same result!

---

### Post by travlemon on 2012-02-06
I can't help but join the bandwagon, and let you know that installing the **python-glade2** package fixed it for me too.  Thanks!

---

