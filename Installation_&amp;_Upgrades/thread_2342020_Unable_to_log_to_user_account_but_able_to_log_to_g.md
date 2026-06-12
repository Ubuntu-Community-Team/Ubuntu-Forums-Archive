---
title: "Unable to log to user account but able to log to guest account"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by mark253 on 2016-11-03
Hi,
after yesterday update, I can log us user but start-up stop with plain wallpaper. I can not start any program and no keyboard shortcut work. When I log on as guest account all is well. What's going on ? What I can do with it ? It's accept the password but start up freeze on plain wallpaper. But the computer do not freeze as I can use mouse. 
Please help.
I have Xubuntu 14.04 with kernel 100. I tried to start with older kernel 98, but it didn't helped.

---

### Post by ubfan1 on 2016-11-03
Maybe the problem is with the hidden "dot" files (ones whose first character is a . ).  The guest account starts with none of them, and so works.  Try logging into a virtual terminal (ctrl-alt-F2)  (F1 through F6 should work, with F7 being the graphical interface).  Then rename (or just delete) the .Xauthority file and .cache directory and see now your login gets to a full desktop.

---

