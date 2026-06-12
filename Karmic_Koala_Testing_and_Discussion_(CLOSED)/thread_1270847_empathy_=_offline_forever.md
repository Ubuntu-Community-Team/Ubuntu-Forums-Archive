---
title: "empathy = offline forever?"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by meborc on 2009-09-20
sorry if this has been posted already... i did a search and did not find anything

ok... so i have karmic alpha 6 with todays updates... i fired up empathy to check out how far is the development gone and i'm unable to set my status other than offline

i can set it from the main window of empathy, but my buddies still see me as offline and the empathy icon on taskbar is saying i'm "hidden"

am i the only one or can anyone confirm this... if so - bug time

---

### Post by taavikko on 2009-09-20
msn-protocol is working correctly here.
Can switch statuses and such and others will see me online.

Can't test other protocols, since I don't have any friends :lolflag:


Still waiting for indicator-session to be able to set the statuses :)

---

### Post by steeleyuk on 2009-09-20
> **meborc said:**
> sorry if this has been posted already... i did a search and did not find anything

ok... so i have karmic alpha 6 with todays updates... i fired up empathy to check out how far is the development gone and i'm unable to set my status other than offline

i can set it from the main window of empathy, but my buddies still see me as offline and the empathy icon on taskbar is saying i'm "hidden"

am i the only one or can anyone confirm this... if so - bug time

I can confirm. Jabber and Bonjour can both be changed but MSN is always hidden, no matter what status I set.

---

### Post by steev182 on 2009-09-20
I was getting this problem too, in the user menu at the top right corner of the desktop I'm offline and can't change that, but in empathy I can change to online or busy, but these changes aren't seen by my friends in msn.

It's a little annoying... well, very annoying.

---

### Post by napsy on 2009-09-20
This bug has been fixed in upstream ([https://bugs.freedesktop.org/show_bug.cgi?id=23635](https://bugs.freedesktop.org/show_bug.cgi?id=23635))

---

### Post by meborc on 2009-09-20
> **napsy said:**
> This bug has been fixed in upstream ([https://bugs.freedesktop.org/show_bug.cgi?id=23635](https://bugs.freedesktop.org/show_bug.cgi?id=23635))

thanks... i guess we'll have to wait for telepathy-butterfly 0.5.1 :D

---

### Post by gnomeuser on 2009-09-20
> **meborc said:**
> thanks... i guess we'll have to wait for telepathy-butterfly 0.5.1 :D

You could do:
sudo add-apt-repository ppa:telepathy/ppa

---

### Post by meborc on 2009-09-20
> **gnomeuser said:**
> You could do:
sudo add-apt-repository ppa:telepathy/ppa

yes... but then i would not be testing vanilla karmic ;)

thanks for the link though (will use it soon)

---

### Post by terry_gardener on 2009-09-20
this happened to me i was always showing as hidden on my side and offline to contacts. 
solved it by uninstalling the telepathy-butterfly package then i was showed as online. 

then when i did updates it installed the telepathy-butterfly package again and it has work ever since.

---

