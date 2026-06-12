---
title: "Cannot turn on compiz in eee pc 1201n after upgrade to Maverick"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by macozz on 2010-10-10
Hi all,
I upgrade to 10.10 via online upgrade yesterday morning. All seems to run fine, and before the yesterday afternoon upgrade, compiz appears disabled and each time I try to enable it I get the error message.
I checked the direct rendering is working. Google Earth works fine also, so all seems to be OK.
Any one has an idea why compiz cannot be turn on and why this start just yesterday?

My system: Eee PC 1201n, Nvidia Ion, 4 Gb Ram, 320Gb HD
Ubuntu Maverick updated.

Thanks!

---

### Post by DayLite on 2010-10-11
> **macozz said:**
> Hi all,
I upgrade to 10.10 via online upgrade yesterday morning. All seems to run fine, and before the yesterday afternoon upgrade, compiz appears disabled and each time I try to enable it I get the error message.
I checked the direct rendering is working. Google Earth works fine also, so all seems to be OK.
Any one has an idea why compiz cannot be turn on and why this start just yesterday?

My system: Eee PC 1201n, Nvidia Ion, 4 Gb Ram, 320Gb HD
Ubuntu Maverick updated.

Thanks!

Many of us are having the same problem.

---

### Post by macozz on 2010-10-11
Well, good to known I am not alone... But, someone foud some sort of workaround?

---

### Post by Rypervenche on 2010-10-11
I have an Eee PC 1201PN and am having the same problem. Compiz was apparently working at first, but I would get a window that would open and close constantly in my bottom panel every time I clicked on a new window.

Since then I have updated my Compiz using the PPA, but now I am having the same problem as you, it won't even start, it gives me an error instead.

Is this a problem with the Beta Nvidia driver or something else? Can anyone help? :(

---

### Post by macozz on 2010-10-11
At first I believed that was a problem with the driver, but since the graphic acceleration is working ans GoogleEarth does work fine, I imagine that is not the driver. But of course I am not sure...

---

### Post by DayLite on 2010-10-11
> **macozz said:**
> At first I believed that was a problem with the driver, but since the graphic acceleration is working ans GoogleEarth does work fine, I imagine that is not the driver. But of course I am not sure...

I think the problem is not with the Graphic Card Driver but with Compiz. I researched it and there is not a compete update to Maverick

---

### Post by bluemoth on 2010-10-12
I had the same problem with my HP Mini 311. I found this website ([http://forum.ubuntu.pl/showthread.php?p=700128](http://forum.ubuntu.pl/showthread.php?p=700128)) in a foreign language and decided to install compiz-gnome. This worked but changing desktops wasn't working. I went to synaptic and installed other compiz packages. Still didn't work. It turned out the default compiz settings were minimal and things needed to enabled to allow switching between desktops.

BTW, check this out:
[http://ilapstech.blogspot.com/2010/10/galaxy-live-wallpaper-like-compiz.html](http://ilapstech.blogspot.com/2010/10/galaxy-live-wallpaper-like-compiz.html)

---

### Post by macozz on 2010-10-15
I am in doubt if mark this as solved.
After some trials, the last one lead me to broke the xserver, I made a fresh install and all seems to run fine now. Compiz works, all the effects are OK...
So, It seems that something goes wrong during the 10.04 to 10.10 upgrade, probably (an just a suspicion) some configuration file left as it was in the original 10.04 caused the compiz not working.

Cheers!

---

### Post by Rypervenche on 2010-10-15
> **macozz said:**
> I am in doubt if mark this as solved.
After some trials, the last one lead me to broke the xserver, I made a fresh install and all seems to run fine now. Compiz works, all the effects are OK...
So, It seems that something goes wrong during the 10.04 to 10.10 upgrade, probably (an just a suspicion) some configuration file left as it was in the original 10.04 caused the compiz not working.

Cheers!

Do you have your / and /home under different partitions or the same?

---

### Post by macozz on 2010-10-15
Different partitions! I adopt this habit many years ago after a disaster that destroy my data completely.

---

