---
title: "Why does wine 1.2 asks to remove ttf-tahoma-replacement?"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-14
it ask for partial update  to remove ttf-tahoma-replacement so what to do?

thanks in advance.

---

### Post by petejk on 2010-04-14
in terminal run 
sudo apt-get remove ttf-tahoma-replacement

now run update-manager to update wine

the font is a recommended package but not an essential one

---

### Post by aviramof on 2010-04-14
ok i removed it and updated wine but now if i want to install it it asks to remove wine and should not happen.

---

### Post by mc4man on 2010-04-14
This will explain
[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/514493](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/514493)

(you should take a look at the changelogs of updates, usually they're informative, many times will list applicable bug(s) in launchpad, ect.

---

### Post by aviramof on 2010-04-14
thanks for your help.

---

