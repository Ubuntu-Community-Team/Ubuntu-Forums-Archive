---
title: "empathy config folder"
date: 2008-08-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Hairy_Palms on 2008-08-28
hey, can anyone tell me where empathy stores its user files? ive scoured my hidden folders in my home directory and .config and cant seem to find it.

---

### Post by aamukahvi on 2008-08-28
```
locate empathy | grep $HOME
```
Will tell you to look in gconf, /apps/empathy.
I don't know what it does with the file downloads, avatars and such.

Also have a look at gconf /apps/telepathy and ~/.mission-control

---

### Post by bruce89 on 2008-08-28
> **aamukahvi said:**
> ```
locate empathy | grep $HOME
```
Will tell you to look in gconf, /apps/empathy.
I don't know what it does with the file downloads, avatars and such.

Avatars are put in ~/.cache/Empathy/avatars.

---

