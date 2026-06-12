---
title: "Will Karmic have Ati Support?"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by prions on 2009-09-29
Jaunty has a problem with not recognizing ATI drivers, leading me to revert to Ibex for the time being. 

But, will Karmic recognize proprietary ATI drivers like Ibex and earlier versions will? 

I'm using an ATI mobility xpress 200m by the way.

---

### Post by tom66 on 2009-09-29
I've used Jaunty, it detected my ATI card fine...

However, I'm not currently using Jaunty because of standby problems.

---

### Post by mattkoehn on 2009-09-29
[http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA](http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA)

This artical leaves me optimistic.

---

### Post by RAOF on 2009-09-29
> **prions said:**
> ...
But, will Karmic recognize proprietary ATI drivers like Ibex and earlier versions will? 

No, because...
> **prions said:**
> 
I'm using an ATI mobility xpress 200m by the way.
is no longer supported by the proprietary fglrx driver, and hasn't been for a couple of fglrx releases.  

On the other hand, it *should* work perfectly well with the default, open-source driver.

---

### Post by Ric_NYC on 2009-09-29
> **prions said:**
> Jaunty has a problem with not recognizing ATI drivers, leading me to revert to Ibex for the time being. 

But, will Karmic recognize proprietary ATI drivers like Ibex and earlier versions will? 

I'm using an ATI mobility xpress 200m by the way.


Same issue here.

I have an ATI Radeon™ Xpress 1200 graphics.

Can't play hd flash videos with good performance.

---

### Post by andrewabc on 2009-09-29
> **prions said:**
> Jaunty has a problem with not recognizing ATI drivers, leading me to revert to Ibex for the time being. 

But, will Karmic recognize proprietary ATI drivers like Ibex and earlier versions will? 

I'm using an ATI mobility xpress 200m by the way.

You should download the beta this Thursday, burn to cd-rw (or put on liveusb) and test to see if your hardware works or not. :)

---

### Post by prions on 2009-09-29
Alright, either way I'll try it out. 

My worry is that I wont be able to boot in Karmic like I did in Jaunty. 

As in, instead of a splash screen I would have a black screen with scattered red and green on the top. Which forced me to downgrade.  

I suspect it was my driver problems, but fglrx would have solved that.

---

### Post by hblaw on 2009-09-29
> **Ric_NYC said:**
> Same issue here.

I have an ATI Radeon™ Xpress 1200 graphics.

Can't play hd flash videos with good performance.

Same here.

---

### Post by ktp on 2009-09-29
> **prions said:**
> Alright, either way I'll try it out. 

My worry is that I wont be able to boot in Karmic like I did in Jaunty. 

As in, instead of a splash screen I would have a black screen with scattered red and green on the top. Which forced me to downgrade.  

I suspect it was my driver problems, but fglrx would have solved that.

you most likely got the red and green screen because you have fglrx installed and the latest driver dropped support for the card.  For some reason, at least during alpha/beta testing, the upgrade process did not work correctly.  I had to manually purge fglrx and then the open-source drivers worked.  There were lots of threads around this in jaunty testing forum.  

I do have to agree that there were lots of issues with open-source ati driver in jaunty.  I got sick of it and installed nvidia but might try the ati driver again because the open-source driver have came a long way.  I mostly want to try the new 3D support, which might be off by default.

---

### Post by prions on 2009-09-29
Yeah, I got it to work once, but soon after I realized it wasn't worth the trouble and downgraded. Ibex has been treating me well. 

But nevertheless I have high hopes for Karmic. :P

---

### Post by Wise Ferret on 2009-09-29
For what it's worth, the open source driver ("radeon") works marvelously for me with a x1600, with beautiful 3d and even with flickerless video while using compiz.

---

### Post by sdowney717 on 2009-09-29
yes it is pretty good, compiz works well. I have an x1300.
I am building a new system and switching to Nvidia.

There is no svideo out yet.

---

### Post by Longinus00 on 2009-09-29
You guys will no longer be able to use fglrx on your older ati cards. There's no way around it, just use the open source drivers. You actually get battery life with the open source drivers (according to phoronix anyway).

---

### Post by misfitpierce on 2009-09-29
Ok well I too have a ATI200 and as said FGLRX will not support it anymore but the opensource xorg-ati driver will(NOT xorg-fglrx) and the opensource one is still going to always get updates and get better over time so don't worry about that. The most recent opensource update made the ati xpress 200m work alot better in glxgears and fixed the lag issue for me. So it should work fine, just don't try to install fglrx as it will mess up your xorg and all you will see is gargled crap on the screen. Opensource for the win! :) enjoy!

---

### Post by inportb on 2009-09-29
> **RAOF said:**
> No, because...

is no longer supported by the proprietary fglrx driver, and hasn't been for a couple of fglrx releases.  

On the other hand, it *should* work perfectly well with the default, open-source driver.

Indeed!

---

### Post by Sand &amp; Mercury on 2009-09-30
> **inportb said:**
> Indeed!
Yep, I've got an xpress 200m as well and the open source driver does the job just fine. Gaming performance leaves much to be desired, but it's not a card that's suited for gaming to begin with.

---

### Post by andrewabc on 2009-09-30
[AMD R600/700 2D Performance: Open vs. Closed Drivers](http://www.phoronix.com/scan.php?page=article&item=amd_r600_r700_2d&num=1)
Open Source Driver wins.

---

### Post by benmoran on 2009-09-30
That comparison is just 2D performance, but the 3D stuff is moving along nicely. Us older r300 guys have had 3d for a while, albeit only OpenGL 1.5. I can't wait for Gallium3D and all that it entails.

---

### Post by pulpo69 on 2009-09-30
what about the people with newer ati-cards (radeon 4870 for example)?
is it better to install fglrx?

---

### Post by Reiger on 2009-09-30
I happen to have a HD4870 in my desktop and I get by with the Open Source driver perfectly fine (it became usable during Jaunty but it is only shaping up to be good now). The really good stuff is yet to come for that architecture, kernel 2.6.32 promises to have much better support for 3D acceleration as well as KMS..

---

### Post by prions on 2009-09-30
Although games arent my main focus anymore, it would be really cool to see the open source drivers working well. 



If steam would only make their client and games linux compatible ;)

And to remove the garble I would have to remove fglrx and solve this problem for good? Cool.

---

### Post by NCLI on 2009-09-30
> **pulpo69 said:**
> what about the people with newer ati-cards (radeon 4870 for example)?
is it better to install fglrx?
If you want 3D, definitely yes(for now).

---

### Post by Longinus00 on 2009-09-30
> **pulpo69 said:**
> what about the people with newer ati-cards (radeon 4870 for example)?
is it better to install fglrx?

As has been previously mentioned, there is not yet any 3d support for the newer (r6xx-r7xx) cards. It's being implemented and if you like living dangerously you can install and test it. [http://www.x.org/wiki/radeonhd%3Aexperimental_3D](http://www.x.org/wiki/radeonhd%3Aexperimental_3D) Realistically, stable 3D support may have to wait until 10.04+1 but we have to wait and see.

---

### Post by benmoran on 2009-10-10
Yeah, these are some really exciting times for Linux users. Having been so far behind the curve with graphics all these years, it's awesome to think that we're getting such cool features. A lot of hard work from a lot of people is finally coming together all at once. 

I guess that's why it took so long in the first place. It was just such a huge undertaking, redesigning the entire graphics system. And all the pieces had to be developed simultaniously. I'm extremely grateful to all the guys contributing. And also to ATI for embracing the open source model.

---

### Post by emarkay on 2009-10-11
Yes,  and there are many posts here detailing it.  FWIW,  Karmic even has a release of Catalyst before everyone else!

---

