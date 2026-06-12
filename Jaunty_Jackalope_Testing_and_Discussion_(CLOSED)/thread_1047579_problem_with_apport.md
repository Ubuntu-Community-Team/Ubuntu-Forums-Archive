---
title: "problem with apport"
date: 2009-01-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-01-22
sudo /etc/init.d/apport stop
 * Stopping automatic crash report generation: apport                           /etc/lsb-base-logging.sh: line 273: runlevel: command not found
/etc/lsb-base-logging.sh: line 278: exit: Stopping: numeric argument required

---

### Post by phorgan1 on 2009-03-06
/etc/lsb-base-logging.sh: line 273: runlevel: command not found

tells you what the problem is.  The bug is in lsb-base-logging.sh.  Edit it, go to line 273, and add /sbin in front of runlevel and it will work.

Patrick

---

