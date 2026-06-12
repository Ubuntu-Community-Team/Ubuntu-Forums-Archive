---
title: "jaunty and ati"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by shrndegruv on 2009-03-30
Do we know yet if it will be possible to use the fglrx drivers on jaunty, with its xorg-server 1.6?  From what I read online we might be up a creek...am I wrong?

---

### Post by mtbsoft on 2009-03-31
All I can say is that my Dell 9400 has the ATI X1400 graphics and it works like a dream with the fglrx drivers.  I installed the beta, loaded ccsm and switched on all the compiz goodies (cube, animations, etc.) I normally use - no tearing or jerkiness, crystal clear even in movies, and not a proprietory graphics driver in sight!

---

### Post by shrndegruv on 2009-03-31
> **mtbsoft said:**
> All I can say is that my Dell 9400 has the ATI X1400 graphics and it works like a dream with the fglrx drivers.  I installed the beta, loaded ccsm and switched on all the compiz goodies (cube, animations, etc.) I normally use - no tearing or jerkiness, crystal clear even in movies, and not a proprietory graphics driver in sight!

you say you use the fglrx driver, then you say no proprietary.  which is it?

i think i have to use the fglrx -- when i installed ubuntu it the driver manager popped up and said i needed proprietary.  

i have an ati 3670 hd card.

---

### Post by uBeer on 2009-03-31
Yes, the propriety driver is included in the repos. The beta 9.4 release to be exact.

Works for the most part, except resume after suspend, but that would be a mobility/laptop problem.

---

### Post by shrndegruv on 2009-03-31
> **uBeer said:**
> Yes, the propriety driver is included in the repos. The beta 9.4 release to be exact.

Works for the most part, except resume after suspend, but that would be a mobility/laptop problem.

i had read that the fglrx driver is not yet compatible with xorg-server 1.6 -- you are saying it works? sweet..

---

### Post by Reiger on 2009-03-31
Yup. The *Jaunty repositories* contain a *beta Catalyst 9.4* driver, which works with X server 1.6.

---

### Post by inportb on 2009-03-31
> **mtbsoft said:**
> All I can say is that my Dell 9400 has the ATI X1400 graphics and it works like a dream with the fglrx drivers.  I installed the beta, loaded ccsm and switched on all the compiz goodies (cube, animations, etc.) I normally use - no tearing or jerkiness, crystal clear even in movies, and not a proprietory graphics driver in sight!

That's pretty confusing; are you using fglrx or not?

---

### Post by shrndegruv on 2009-03-31
> **Reiger said:**
> Yup. The *Jaunty repositories* contain a *beta Catalyst 9.4* driver, which works with X server 1.6.

giggity.  i hope they clear up the resume from suspend issues.  I miss my nvidia card. :(

---

### Post by mtbsoft on 2009-03-31
> **inportb said:**
> That's pretty confusing; are you using fglrx or not?
Sorry, you're right, I don't know what I was thinking when I typed that - the fingers didn't type what I meant them to, there should obviously have been some "withOUT"s in there.  

To clarify, I'm using only the inbuilt drivers, no proprietory drivers but everything works as well (if not better, I feel) than 8.10 with the proprietory drivers.  

Sorry for the confusion.

---

### Post by Maxei on 2009-04-05
> 
inportb:
"That's pretty confusing; are you using fglrx or not?"

mtbsoft:
"Sorry, you're right, I don't know what I was thinking when I typed that - the fingers didn't type what I meant them to, there should obviously have been some "withOUT"s in there.

To clarify, I'm using only the inbuilt drivers, no proprietory drivers but everything works as well (if not better, I feel) than 8.10 with the proprietory drivers."

Sorry for the confusion. 

Lol. Still confused, aren't you? :lolflag: You are indeed using the proprietary beta catalyst 9.4 which provides the fglrx driver. Even if you got it from one of the ubuntu (?) repositories, it is still proprietary.
By the way, I'm glad it works for you. I still use an older driver version which has no 3D support. I'll give it a try when the final  9.4 comes out. cheers.

---

### Post by aamukahvi on 2009-04-05
> **Maxei said:**
> Lol. Still confused, aren't you? :lolflag: You are indeed using the proprietary beta catalyst 9.4 which provides the fglrx driver. Even if you got it from one of the ubuntu (?) repositories, it is still proprietary.
By the way, I'm glad it works for you. I still use an older driver version which has no 3D support. I'll give it a try when the final  9.4 comes out. cheers.
Since Catalyst 9.4 doesn't even support the X1400, he's probably using the open source drivers.

---

### Post by mtbsoft on 2009-04-05
> **Maxei said:**
> Lol. Still confused, aren't you? You are indeed using the proprietary beta catalyst 9.4 which provides the fglrx driver. Even if you got it from one of the ubuntu (?) repositories, it is still proprietary.
Confused indeed since going to the hardware drivers applet shows NO proprietory drivers in use and xorg.conf shows nothing about ATI or flgrx.

```

Section "Device"
    Identifier "Configured Video Device"
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor    "Configured Monitor"
    Device     "Configured Video Device"
EndSection

```

As for where I got the drivers from, they are the "built-in" which were installed as part of the standard install, I didn't do anything to get them so they came from the Ubuntu Jaunty repositories.  That said, it is interesting to note that the Software Sources dialog shows a tick against *Proprietory drivers for devices (restricted)* which I have not ticked myself - I don't recall any of the previous distributions having that option ticked on release - perhaps it's a beta feature.

> **aamukahvi said:**
> Since Catalyst 9.4 doesn't even support the X1400, he's probably using the open source drivers.
Sounds like a definative answer, thanks for the clarification.

---

### Post by warmotor on 2009-04-06
I installed the fglrx drivers with my X800PRO system. Of course, instead of a login screen I now get two inches of whatever random junk is in my video buffer and a frozen computer. Yippee.

I'm noticing, like the post above, when I check out my xorg.conf on the offending install with the LiveCD (because my other Linux installs can't see ext4, EFF YEAH!) it looks pretty empty. "configured hardware"? is xorg.conf still relevant? Am I hallucinating?

---

