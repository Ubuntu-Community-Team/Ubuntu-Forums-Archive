---
title: "High CPU / Extremely Laggy Compiz"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Diggs808 on 2009-09-10
Okay, 
I don't know if anyone else has seen this problem just yet.  I have searched and there is not a whole lot here or on Launchpad, though I wanted to check prior to posting a bug.  

I am running a Dell Latitude D820 with an NVidia GeForce 7300 (256MB).  Prior to Karmic, I never had any trouble with Desktop effects.  Now, when I enable even the "Normal" my desktop runs incredibly slow.  I have upgraded my Nvidia drivers to 190.32 and have checked everything possible in compiz.  

I did notice that while running top that Compiz is using 50-60% of the CPU.  On Jaunty, it normally uses 3-4%.  

I have attached a screenshot of top.  

Any ideas??

---

### Post by henriquemaia on 2009-09-10
Same thing here. This was the first thing I noticed upon upgrading (this afternoon). Is there any solution?

---

### Post by sylvester_0 on 2009-09-10
Did you get the .190 drivers from nVidia's site and install them manually or use the PPA? I was using the PPA a while ago but ran into problems with DKMS not being able to compile the modules properly whenever I did kernel upgrades so I downgraded to the "official" .185 in the Ubuntu repos and haven't had any problems since. My performance is extremely snappy :)

---

### Post by Diggs808 on 2009-09-10
thanks for all the helpful info.  Looks like I am not the only one having this problem....  :-)  (Glad to know that I am not going crazy!)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/391461](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/391461)

---

