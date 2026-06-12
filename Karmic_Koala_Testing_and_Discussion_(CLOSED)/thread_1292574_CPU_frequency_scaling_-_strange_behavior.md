---
title: "CPU frequency scaling - strange behavior?"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by forcecore on 2009-10-16
Scaling starts on performance mode then keeps CPU on maximum power and manual change is needed to ondemand or whatever mode you want back before you started/restarted computer, anyone had this type problem yet?

---

### Post by wilee-nilee on 2009-10-16
It should by default be running in on demand.

---

### Post by humphreybc on 2009-10-25
I've also got this problem. I can't seem to fix it by changing settings in gconf-editor either. Any word on if this is going to be fixed in the final release?

EDIT: Actually, it seems this is on purpose and it should switch to ondemand after 60 seconds.

> 
Ubuntu starts with "performance" governor most likely to reduce boot-up time, then when it's safe to do so (60 seconds), start saving power.


See this thread for more information:
[http://ubuntuforums.org/showthread.php?t=1143506](http://ubuntuforums.org/showthread.php?t=1143506)

---

