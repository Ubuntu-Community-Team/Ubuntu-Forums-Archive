---
title: "X server fails to start after upgrade from 8.04 to 8.10"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by sethtriggs on 2009-11-26
After a reasonably successful upgrade of my laptop from 8.04 to 9.10 (it took a while), I foolishly decided to try the same with my desktop.

The desktop is running a new ATI Radeon HD 3650 card (the NVidia GEForce died so the only AGP card I could get on short notice was ATI).

Well, I got that tweaked to run just by not having the restricted drivers run.

Now I ran through the upgrade from 8.04. All seemed to go well till the fateful restart.

The familiar Ubuntu splash screen/loading bar showed up. The loading bar made it all the way to the end. Suddenly, my floppy drive light came on. X never started. And then my monitor's power light shifted to amber, indicating a lost connection.

I tried from recovery console, tried to boot the older kernels in regular mode, tried fixing X server...no dice. The only thing I can reach is the recovery console. Even worse, I have no Internet access so I'm limited in what I can do.

What I'd like to figure out is how I can get this configured such in the console that I can get to the X server! What is so special about the splash screen that it displays but the X Server won't? Is there something that I can do, to even force low-graphics mode?

Any help at all is most appreciated!


lspci -nn | grep VGA reports:

01:00.0 VGA compatible controller [0300]: ATI Tecnologies Inc RV635 PRO AGP [Radeon HD 3650] [1002:9596] 

-Seth

---

### Post by sethtriggs on 2009-11-26
I was able to save the day.

First thing was to get into the Recovery Console and edit xorg.conf with the values found here:

[http://ubuntuforums.org/showthread.php?t=994711](http://ubuntuforums.org/showthread.php?t=994711)

Those were "wrong" enough to trigger low-graphics mode. By starting Ubuntu anyway, you'll end up going to a very crude-looking desktop. From there, if the internet still works, you can then install the restricted drivers.

I am DEFINITELY not going to 9 with this ATI Radeon HD3650. If any of you out there have this card, Do not try to upgrade, or it'll be a nightmare like what I've endured!

-Seth

---

