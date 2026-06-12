---
title: "Unity 2d disable compositing"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by moljac024 on 2011-10-13
I just tried 11.10 with unity 2d (since I have a very old intel gsm945 card) and I have one question...

How and WHY does unity 2d have compositing?! That defeats the whole purpose of lightweightness. I expected unity 2d to be, well you know, 2d. A friend installed unity 2d on his laptop with Ubuntu 11.04 and it doesn't have compositing there, which is what I would expect.

But when I booted into unity 2d I had these fancy fade-out and fade-ins, fancy blurred transparency etc. which made it just a tad less sluggish than full blown compiz-enabled unity. I didn't have more time to test but I reckon Unity 2d uses metacity with compositing enabled?

If that's the case, gconf-editor should be able to disable it, and I wonder why it was default on 11.04 but not on 11.10

---

### Post by PhilLord on 2011-10-20
Did you manage to achieve this by any chance. 

I have the same problem here. Relatively old hardware on some of my machines. Unity 2D runs slower than in the past, with a struggling fan. Aside from which I don't like transparency and shadows. I spend money on good glasses so I don't get blurry vision; why would I want it back?

Phil

---

### Post by newbiefly on 2011-10-21
been having the same problem.  

ppl suggested "dconf-editor" i guess it must be a typo cause i cant find it anywhere.  tried gconf-editor but it wasn't any help and i guess it shouldn't be cause the whole point of this mess is getting away frome gnome.

after hours of research and pain i have the solution 
[http://marianochavero.wordpress.com/2011/10/14/unity-2d-settings-ui-for-ubuntu-11-10-oneiric-ocelot/](http://marianochavero.wordpress.com/2011/10/14/unity-2d-settings-ui-for-ubuntu-11-10-oneiric-ocelot/)
**[http://dl.dropbox.com/u/3559201/unity-2d-settings/unity-2d-settings-1.0-oneiric1.deb]("http://dl.dropbox.com/u/3559201/unity-2d-settings/unity-2d-settings-1.0-oneiric1.deb")
**be sure source code is checked in software sources (saves a lot of pain)
**install it
**run it
**uncheck "enable compositing"
**live well and enjoy lag free mines or in my case relatively lag free

much love for my low end coputer using brothers and sisters 
and a very special thanks to Mariano Chavero for writing this little editor. 
do you guys think it should be proposed for 12.04?

---

