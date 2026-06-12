---
title: "[SOLVED] I want to save in /etc/apt/sources.list"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by mahinda on 2008-02-29
I want to save some code in /etc/apt/sources.list   but it say I do not have permissions to do so, probable I need to log as root, but I don't know how to do this.

please tell me simple way, I am new to here.

---

### Post by jan quark on 2008-02-29
run in terminal

```
gksudo gedit /etc/apt/sources.list
```

should work now

---

### Post by banewman on 2008-02-29
For security/system safety there is an admin level that is reached with a password - sudo (typed in a terminal (gksu for graphical apps) ) is how your user reaches that level.

---

### Post by Pumalite on 2008-02-29
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

