---
title: "Stop mysql service"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by omar.bilani on 2010-03-01
Hi, i have installed mysql and its running fine.
i need to know how i can stop mysql from auto starting when i start my machine.
thanks.

---

### Post by quixote on 2010-03-02
If you go to System > Preferences > Startup Applications, is mysql listed there, and is it checked?  If so, uncheck it, and that should stop it from loading on startup.  If not, we'll have to dig deeper.

---

### Post by adam814 on 2010-03-02
It's started by upstart.  I don't know if there's a more effective or better way, but you can use sysv-rc-conf (from the package of the same name) to turn it off in whatever runlevels you want to.

---

