---
title: "AR5007 not finding networks since yesterdays update"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by blakamin on 2008-09-26
Network Manager will not find any wireless routers and if you manually select a new one, the "connect" box is greyed out. 

???

---

### Post by beren.olvar on 2008-09-26
are you using ndiswrapper??
if thats the case try reloading it:

sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

sometimes i have to do that in order to get it work again
cheers

---

### Post by blakamin on 2008-09-26
> **beren.olvar said:**
> are you using ndiswrapper??
if thats the case try reloading it:

sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

sometimes i have to do that in order to get it work again
cheers
Unfortunately, I'm not.
I'm using the restricted drivers
but it gets worse, now AWN wont work without a python crash!
LOL
Might have to roll back to hardy 
After the last 2 days of updates, things are 10 times worse than the first alpha6 six release!

---

### Post by Nullack on 2008-09-26
Its your choice :) though personally I find it fun to have new stuff break and a new round of bug reports, looking into why it broke, and getting goodness come in with fixes. You *can* make a difference :)

---

### Post by blakamin on 2008-09-26
> **Nullack said:**
> Its your choice :) though personally I find it fun to have new stuff break and a new round of bug reports, looking into why it broke, and getting goodness come in with fixes. You *can* make a difference :)

I know!!!! I reaaally want to go forward and report 5 a day but I cant if my wireless doesn't work (I do my best thinking laying in bed using my wireless!):(

---

### Post by blakamin on 2008-09-26
Back!
After a re-install and an update and some playing with wicd and NM0.7 I switched off. 1am.
8 am I get up and now it works!:confused:

Oh well... time to find other bugs

---

