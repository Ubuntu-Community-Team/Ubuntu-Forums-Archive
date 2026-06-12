---
title: "gnome-settings failed to start"
date: 2009-01-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by thor2002ro on 2009-01-03
gnome-settings-[7272]: segfault at 4 ip b7037b2b sp bfc286e0 error 4 in libgnome-desktop-2.so.11.0.0[b701f000+20000]

dmesg reports this when the gnome settings daemon attempts tp start can anyone tell me whats wrong?

---

### Post by bpl07 on 2009-01-03
Delete ~/.config/monitors.xml

[https://bugs.launchpad.net/gnome-settings-daemon/+bug/309602](https://bugs.launchpad.net/gnome-settings-daemon/+bug/309602)

---

### Post by thor2002ro on 2009-01-03
omg TKS i had this problem for so long ....

---

