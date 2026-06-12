---
title: "Problem starting up X"
date: 2014-06-03
forum: Installation &amp; Upgrades
---

### Post by fkrogh2 on 2014-06-03
This is a new install of 14.04.  Sometimes system boots into X just fine.  Other times it stops with a screen with some dots in diagonals.  Typing <cntrl> <alt> <F?> where ? is any digit but 7, followed by   <cntrl> <alt> <F7> and all is well.  I'm hoping there is some thing to try that will get this working properly all the time.  I am using the nvidia drivers.  Thanks,
Fred

---

### Post by fkrogh2 on 2014-06-03
Found a fix.  Inserted a line "sleep 2" just before "exec lightdm" in file /etc/init/lightdm.conf.  Evidently this problem has to do with using an SSD.

---

