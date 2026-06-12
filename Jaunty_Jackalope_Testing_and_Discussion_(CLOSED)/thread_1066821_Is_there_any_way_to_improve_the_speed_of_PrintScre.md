---
title: "Is there any way to improve the speed of PrintScreen?"
date: 2009-02-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-02-11
Hi!

After I press printscreen it will take ~6-7 seconds for the shot to take, am I the only one with this low speed?

---

### Post by MacUntu on 2009-02-11
No problem here.

---

### Post by taavikko on 2009-02-11
> **olskar said:**
> Hi!

After I press printscreen it will take ~6-7 seconds for the shot to take, am I the only one with this low speed?

Try
```
gconftool-2 -s /apps/gnome-screenshot/delay -t int 0
```
Hope it helps.

---

### Post by olskar on 2009-02-11
> **taavikko said:**
> Try
```
gconftool-2 -s /apps/gnome-screenshot/delay -t int 0
```
Hope it helps.

Wow! Thanks! Why isn't that default?

---

### Post by taavikko on 2009-02-11
> **olskar said:**
> Wow! Thanks! Why isn't that default?

It's supposed to be... 
Clean install or upgraded from Intrepid?

Always happy to be some assistance :)

---

