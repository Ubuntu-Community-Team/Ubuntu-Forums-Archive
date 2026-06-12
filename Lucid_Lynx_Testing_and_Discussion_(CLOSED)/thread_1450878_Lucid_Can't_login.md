---
title: "Lucid: Can't login"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bluestar14 on 2010-04-09
after i install lucid beta one, and i think upgraded to beta 2(there was no way to be sure),  i activated the nvidia-96 display driver, which was supposed to be supported in beta 2, i then restart, and everything goes fine until i click my name, then the computer freezes, and the screen goes black and then returns showing the screen before i clicked my name, is this because i was in beta one?(to upgrade to beta 2, i did "sudo apt-get upgrade", and then "sudo apt-get dist-upgrade"..is that the right way?) the bottom line is...I NEED MY LUCID!!!( and my nvidia graphics)

---

### Post by Rocket2DMn on 2010-04-09
Moved to Lucid Lynx Testing and Discussion.  It sounds like X is crashing when you try to login.  Restricted drivers are often a problem in development releases, but I'll let the testers in this forum help you out further.

---

### Post by bluestar14 on 2010-04-09
thanks, so x being the nvidia x11 thing?

---

### Post by jrothwell97 on 2010-04-09
This is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200").

---

