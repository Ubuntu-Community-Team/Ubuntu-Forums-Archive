---
title: "No GUI after installing latest patches for Alpha 5 and Alpha 6"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mareczek1982 on 2009-09-23
Hi..
Yesterday I installed patches for Alpha 5 and after reboot I don't have GDM login, Karmic starts in text mode.. I have to enter Ctrl Alt F7 to start GUI. After dist-upgrade situation is the same..
Did you have the same problems ?

---

### Post by TDK800 on 2009-09-23
had the same problem, after doing sudo aptitude update and sudo aptitude upgrade the problem got fixed...


I am still having the problem of gnome-panel not loading though, both in 9.10 and now it seems also in 9.04, weird.

how can i add gnome-panel and other programs to startup through terminal with the 9.10's upstart or init or whichever it uses.

---

### Post by moviemaniac on 2009-09-23
Same here... didn't try Ctrl+Alt+F7 but "sudo restart GDM" did the trick for me.

---

### Post by coolzire on 2009-09-23
I have this issue with both 2.6.31-9 2.6.31-10 but not with a kernel a compiled myself. I think i compiled from ubuntu source 2.6.31-10.34 .

---

