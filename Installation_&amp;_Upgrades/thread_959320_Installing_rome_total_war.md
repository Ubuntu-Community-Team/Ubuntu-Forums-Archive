---
title: "Installing rome total war"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by jafar3001 on 2008-10-26
Hey I have a problem.  Im trying to install total war through wine, and it works fine up until it tells me to put the second cd in.  When I try to take out the first cd, I get this message, "An application is preventing the volume 'Rome_TW_CD1' from being unmounted." and it wont let me take out the first cd.  Can anyone help me solve this problem.

Thanks

---

### Post by geezerone on 2008-10-26
I tried installing RTW to no avail.

To get past your problem, open a terminal and type:

```
wine eject d:
``` if memory serves me right. :(

---

### Post by jafar3001 on 2008-10-26
when I typed that it said  unable to find or open device for: `[-a]'. Any ideas??

---

### Post by jerome1232 on 2008-10-26
well try wine eject by itself

if that doesn't work pull up winecfg and click on the 'drives' tab see what letter is assigned to your cdrom and then 'wine eject' that

---

### Post by geezerone on 2008-10-26
> **jafar3001 said:**
> when I typed that it said  unable to find or open device for: `[-a]'. Any ideas??

I was nearly right lol - do:

```
wine eject d:
```

Good luck with install!

---

### Post by jafar3001 on 2008-10-26
Alright, I got it to install finally.  Now I can't get it to play.  When I start it, it says error: filename doesn't exist data/animations/SG 01 idle 01.cas.  Whats wrong this time.  Sorry for all the questions, im new to ubuntu and not very computer literate. 

Thanks

---

### Post by geezerone on 2008-10-26
That is precisely the error message I got and after searching never got a resolution. I gave up and stuck with XP for the game tbh. Hope someone can shed light on it though.

---

### Post by jerome1232 on 2008-10-26
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4496&iTestingId=26130](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4496&iTestingId=26130) 

Well from  reading that (btw always check there about your apps when you are trying to run them through wine) it only kind of works, sounds like it's looking for a file do you have the first cd inserted when you start the game? Maybe it needs a file on the cd.

---

### Post by jafar3001 on 2008-10-26
Ya the first cd is in.  It looks like everyones having problems with this game.  I guess i'll have to wait till wine comes out with a newer versions that fixes the problem.

Thanks everyone

---

