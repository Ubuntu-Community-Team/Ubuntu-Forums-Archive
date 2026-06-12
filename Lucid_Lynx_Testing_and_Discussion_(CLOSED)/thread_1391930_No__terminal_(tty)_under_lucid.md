---
title: "No  terminal (tty) under lucid"
date: 2010-01-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SanglierDesBois on 2010-01-27
I've install lucid, and I have no tty. xorg is starting, but if I switch to ctrl-alt-f1, I see the startup output, but no tty login, and nothing in ctrl-alt-f2 +...
??

I've updating the system on a day to day basis, and the problem remain from the begining..

---

### Post by Mark Phelps on 2010-01-27
You do know that Lucid is in early Alpha stages, meaning, LOTS of stuff is unlikely to work!  

Have you checked the release notes to unsure this is not one of the known deficiencies?

---

### Post by VMC on 2010-01-27
> **SanglierDesBois said:**
> I've install lucid, and I have no tty. xorg is starting, but if I switch to ctrl-alt-f1, I see the startup output, but no tty login, and nothing in ctrl-alt-f2 +...
??

I've updating the system on a day to day basis, and the problem remain from the begining..

what output do you get from "who -a":
```
$ who -a
           system boot  2010-01-27 15:34
           run-level 2  2010-01-27 15:34
LOGIN      tty4         2010-01-27 15:34              1098 id=4
LOGIN      tty5         2010-01-27 15:34              1101 id=5
LOGIN      tty3         2010-01-27 15:34              1109 id=3
LOGIN      tty6         2010-01-27 15:34              1113 id=6
vmc      + tty7         2010-01-27 15:34  old         1206 (:0)
LOGIN      tty1         2010-01-27 15:34              1349 id=1
LOGIN      tty2         2010-01-27 15:36              1755 id=2
vmc      + pts/0        2010-01-27 15:36   .          1765 (:0.0)

```

---

### Post by SanglierDesBois on 2010-01-28
X is not working, and I have 0 terminal, so I can't give any command...

---

### Post by Ibidem on 2010-01-29
Sounds like the issue is that X is giving you a black screen (becoming unresponsive), not that the tty stuff is buggy.
Some folks have it, others don't; it might be a graphics card/driver issue.  What card are you using?

If it is a buggy driver, one possible workaround is to rename /etc/X11/xorg.conf if it exists, or to remove the standard driver in a package manager.  These steps will force X to use the vesa/fbdev drivers.  
Please check the card before doing these, though...

Ibidem

---

### Post by chuckyp on 2010-01-29
I just tried to switch to a tty to see if mine was working. My system frozen had to due a hard reset. Looks to be kind of buggy atm.

---

