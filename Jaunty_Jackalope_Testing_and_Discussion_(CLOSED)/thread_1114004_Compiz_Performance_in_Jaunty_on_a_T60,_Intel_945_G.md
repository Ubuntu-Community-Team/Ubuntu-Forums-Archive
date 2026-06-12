---
title: "Compiz Performance in Jaunty on a T60, Intel 945 Graphics Card"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bademeister on 2009-04-02
Hi there,

I just upgraded to Jaunty Beta amd64 on a T60 Lenovo Thinkpad with 2gigs of Ram, a Centrino Core Duo and the Intel 945 Graphics Adapter. I have noticed a serious performance degrade in the Compiz 3d Desktop. 

This used to (on Intrepid 8.10) run very smoothly on my machine but now its is just very sluggish. You can almost see it moving from one frame to the next when using e.g the Magic Lamp effect to minimize something, switching between workspaces or when using the scale plug-in to switch tasks.

Has anyone else experienced this? I am thinking that the likely cause is a driver update(?)
cheers
bademeister

---

### Post by TrueTom on 2009-04-02
This is normal. You can enable UXA to get some better performance but this will lockup randomly with the default Jaunty drivers.

---

### Post by smbm on 2009-04-02
Intel graphics definitely seem a little more sketchy this time round in general to me.

When the final version is released I'm going to mess around to try and build the newer ones from source I think.

---

### Post by bademeister on 2009-04-03
Ok, I see. From what I've been reading it seems that UXA was never atually working. How come I had a much better experience in Gutsy, Hardy, and Intrepid then?
thx
Paul

---

### Post by bademeister on 2009-04-03
Ok, just enabled UXA as described here: [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)
Right now I am back to my previous user experience and haven't experienced any breakage yet, but I realize it's pretty experimental. 
Maybe I can contribute a little through bug reports, we'll see...

---

### Post by diebels on 2009-04-03
As an alternative you can keep running EXA, and boost the performance with this line:
```
        Option          "EXAOptimizeMigration"          "true"
```
Not sure if it locks up less though.

---

### Post by bademeister on 2009-04-03
Hey diebels,

thanks for the hint, i'll give it a go if I experience much breakage. Up to now everything is going fine though.
cheers

---

### Post by asuastrophysics on 2009-04-12
> **diebels said:**
> As an alternative you can keep running EXA, and boost the performance with this line:
```
        Option          "EXAOptimizeMigration"          "true"
```
Not sure if it locks up less though.

this above step completely disabled compiz and now no desktop effects can be enabled ](*,)](*,)](*,)](*,)

is there some way of installing my nvidia proprietary drivers?
i already completely removed the "nouveau" driver. it wasnt working.
for some reason to install my nvidia drivers is now all the sudden impossible in jaunty. under "hardware drivers", nothing is listed for the graphics driver 

....

---

### Post by binbash on 2009-04-12
i was getting crap performance till enabling uxa :

[Enable UXA at ubuntu jaunty]("http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html")

---

