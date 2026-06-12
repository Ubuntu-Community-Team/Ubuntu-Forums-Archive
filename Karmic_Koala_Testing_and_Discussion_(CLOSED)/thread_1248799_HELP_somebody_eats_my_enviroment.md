---
title: "HELP: somebody eats my enviroment"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-08-24
Up to date Kubuntu Karmic is in use. I have removed kdm from services. After logging in via console I check

echo $MY_VAR

- it is defined (as it is defined in ~/.profile). OK, I start KDE via startx, check $MY_VAR in Konsole - it is **not** defined anymore!!

Help!

---

### Post by ilna on 2009-08-24
Renaming .profile to .bash_profile changes nothing.

---

### Post by apmcd47 on 2009-08-24
do you have [PHP]export MY_VAR[/PHP]in your .bash_profile?

Andrew

---

### Post by ilna on 2009-08-24
> **apmcd47 said:**
> do you have [PHP]export MY_VAR[/PHP]in your .bash_profile?

Andrew
Thanks, it helped!

also Andrew ;-)

---

