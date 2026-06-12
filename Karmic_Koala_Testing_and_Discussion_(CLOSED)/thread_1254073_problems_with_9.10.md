---
title: "problems with 9.10"
date: 2009-08-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pvillestang on 2009-08-30
So I just updated to 9.10 to try out the new Kernel for some hardware compatability issues.  Well, I select my user name, and try to boot into GNOME, and I can't.  It shows the Ubuntu splash screen like it's loading the OS, then goes right back to the loading screen.  KDE seems to work, but I'm not a fan of the environment.  Any ideas how to get my GNOME back up and working?

PS

---

### Post by psyke83 on 2009-08-30
It may be compiz. Switch to a VT and temporarily rename /usr/bin/compiz or /usr/bin/compiz.real, then try to login again.

---

### Post by pvillestang on 2009-08-31
Thanks a million man!  I renamed compiz using Ubuntu Live CD, and I was able to reboot into GNOME.  I'm definitely not a fan of the KDE environment.

---

### Post by taurusian on 2009-09-01
This worked for me too. Thank you :D

---

