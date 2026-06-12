---
title: "Screen is all blury and stuff."
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by emshains on 2008-05-01
I had everything going in Gutsy. 


Now in Hardy my screen is like blury. I have set the resolution to 1280x1024 and 32 bit colors. But it feels like, mmm, it was a bit bleached. 


And emerald isnt working, reflection effect isnt adjustable and awn terminal add-on isnt quite working.

---

### Post by emshains on 2008-05-02
It seems I have asked a stupid question and hardy comes with the blury poc* or nobody has had a problem/sees it as a problem, OR nobody gives a crap. 

Well thanks Hardy, now I can use my computer no more than 30 minutes before my eyes go watery.

---

### Post by ansicplusplus on 2008-05-02
Hy, I guess hardy didn't detect your graphics card and switched to a "failsafe" 800x600 resolution. Try ```
gksudo displayconfig-gtk
``` to configure your display manually.
Yours, ansicplusplus

---

### Post by emshains on 2008-05-04
> **ansicplusplus said:**
> Hy, I guess hardy didn't detect your graphics card and switched to a "failsafe" 800x600 resolution. Try ```
gksudo displayconfig-gtk
``` to configure your display manually.
Yours, ansicplusplus

I choose the right display/monitor settings and it is now bleeding edge sharp. Although I dont understand why did I have to do this, because my other  computer which is also pluged into this ViewSonic VP171s didnt have to do this. It even has a worse video card (Radeon 9600), than the one that needed configuration (Nvidia 7300GT). 

Oh now the login screen isnt fitting (like I see only a quater of the screen) but atleast I can write my log and pass, so it woudnlt bother me at everyday use, but If I need to (for instance) swith sesions, how the hell I am going to do that. Thanks for the help.

---

