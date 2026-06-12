---
title: "only the coffee screen after installed dapper"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by kaktos on 2006-07-12
I installed dapper successfully from the alternative cd ,but when launch the system,after
I entered my username and password,the screen stayed there with a mouse pointer and a coffee backgroud.
So,I think maybe it's a problem with the gnome and my hardware,anyone else could help me?

Sorry for my poor English...

PS:Athlon1800+ & nVidia MX4 440

---

### Post by angkor on 2006-07-13
Could you post the output of /home/kaktos/.xsession-errors.

Log in until you get the brown screen and press Ctrl+Alt+F1 and log in at the terminal. Then type:

```
cat .xsession-errors
```

See if you have any errors and post them here.

---

