---
title: "intel graphics performance - again :("
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Stetzen on 2009-08-19
I've been experiencing it since clean install of alpha2, but now I've booted from Hardy LiveDVD and done some benchmarking.

Extreme Tux Racer IS a benchmark, isn't it?

Game settings: all graphics extras are disable, except from FPS; 800x600 resolution.

Hardy: ~60 FPS
Karmik: ~20 FPS

3 times drop!

glxgears (definitely not a benchmark, but...)

Hardy: 4200 frames in 5 secs
Karmik: 1400 frames in 5 secs

3 times drop again. And compiz feels slower as well.

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)


Does anyone else experiencing this issue? The bugreport is closed with "fix released", but this is not fixed for me.

---

### Post by Jay_Bee on 2009-08-19
I noticed that the Caster demo is so slow its unplayable.

---

### Post by Stetzen on 2009-08-19
Filled a new bugreport on launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073)

---

### Post by psyke83 on 2009-08-19
Try the xorg-edgers drivers (if and only if you're prepared to deal with breakage, and know how to downgrade packages). My 855GM chipset's 3D performance is halved with the Karmic drivers (a regression introduced with the 2.6.31 kernel), but the latest drivers have restored performance.

If the edgers drivers work better for you, then you can be fairly confident that Karmic's drivers will also work better in the future.

---

### Post by Stetzen on 2009-08-19
It looks like driver and mesa from xorg-edges do not solve the problem

---

### Post by Compintuit on 2009-08-19
I seem to be the oddball out here - never before have I been able to run compiz with more then a couple frames a second. Now, it darn impressive. I have a pathetic intel integrated card, with I think 32MB memory, and even desktop cube gives me a hard time catching each frame! I was intending on only trying out the karmic beta, but with a spherical desktop cube! Nope, bye bye linux mint, it seems I'm now running a super unstable alpha. Oh, for graphics...

---

### Post by Jay_Bee on 2009-08-26
this is fixed for me with the latest mesa updates, I get around 40fps in Extreme tux racer and Caster 3d is fast and without visual corruption.
:D

---

### Post by Stetzen on 2009-08-26
Yes, with a new mesa everything seems to be faster, but still is not as fast as it can be and as it was. I've got around 30-35 fps with extremetucracer.

---

### Post by HankB on 2009-08-26
> **Stetzen said:**
> 
Extreme Tux Racer IS a benchmark, isn't it?


Pardon my ignorance on this. How do you run etracer as a benchmark? I have installed it and when I run 'etracer -a' it goes to a "highscore" page.

thanks,
hank

---

### Post by Stetzen on 2009-08-26
> **HankB said:**
> Pardon my ignorance on this. How do you run etracer as a benchmark? I have installed it and when I run 'etracer -a' it goes to a "highscore" page.

thanks,
hank

There is a checkbox within the game itself (configuration -> graphics), which is called "show FPS". Frames per second count will be displayed in the left down angle of the screen.

---

### Post by HankB on 2009-08-26
> **Stetzen said:**
> There is a checkbox within the game itself (configuration -> graphics), which is called "show FPS". Frames per second count will be displayed in the left down angle of the screen.

I've tried that. The results vary with the scenery and don't seem consistent from one run to the next, even with no user input. I'm not sure how to get comparable results that way.

-hank

---

### Post by Jay_Bee on 2009-08-27
I don't know, I just play the first map and than I see the average fps on that map. I wouldn't call it a benchmark, but it's better than glxgears.
I am happy that the performance is getting better, it still isn't as good as Hardy's but it's completly usable for me.

---

