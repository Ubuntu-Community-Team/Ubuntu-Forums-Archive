---
title: "[intrepid-alpha-2] running file-roller as root destroys permissions on /"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by fahrenheit_210 on 2008-07-26
Xubuntu intrepid development branch
Kernel 2.6.26-4
file-roller 2.23.4

Running file-roller as root removes permissions from the root of the filesystem which results in a complete failure of the system since nothing can be read and no commands can be executed.  System can be restored by resetting permissions with "chmod 755 /" in recovery mode.

---

### Post by tamoneya on 2008-07-26
how did you invoke file roller as root.  Did you use sudo or gksudo.  since it is a graphical application make sure you use gksudo.

---

### Post by Sef on 2008-07-26
Moved to Intrepid Ibex Testing and Discussion.

---

### Post by ronacc on 2008-07-26
this is probably related to my bug #250021 , if it is related using gksudo does not help .

---

### Post by Nullack on 2008-07-26
Please make sure you either add your scenario to existing bugs or do a new bug report as thats pretty serious

---

### Post by ronacc on 2008-07-26
it looks like performing some actions as root changes the permissions of / to 700  , in my case it was using a root nautilus to copy some files , the OP is correct changing the permissions of / back to 755 restores the system .

---

