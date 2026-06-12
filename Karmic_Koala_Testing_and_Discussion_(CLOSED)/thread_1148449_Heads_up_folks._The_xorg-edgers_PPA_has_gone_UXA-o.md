---
title: "Heads up folks. The xorg-edgers PPA has gone UXA-only for Intel graphics."
date: 2009-05-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-05-04
EXA and DRI1 have been removed.

Expect occasional X freezes and general frustration.

---

### Post by portis on 2009-05-04
For me, the occasional freeze became extremely rare after I turned of compiz.

---

### Post by artir on 2009-05-04
That's because Intel dropped anything but UXA from their drivers

---

### Post by Starks on 2009-05-04
> **artir said:**
> That's because Intel dropped anything but UXA from their drivers
Yes, I know, I've been following.

---

### Post by olskar on 2009-05-04
> **Starks said:**
> EXA and DRI1 have been removed.

Expect occasional X freezes and general frustration.

I'm used to it, using Jaunty you know ;)

---

### Post by caryb on 2009-05-04
Being a Nvidia user I wished I had read about this before I upgraded my wifes laptop from Intrepid to Jaunty. She now has mine & I'm stuck with hers freezing all the time. I think it's time to go to vesa.


Cary

---

### Post by olskar on 2009-05-05
> **caryb said:**
> Being a Nvidia user I wished I had read about this before I upgraded my wifes laptop from Intrepid to Jaunty. She now has mine & I'm stuck with hers freezing all the time. I think it's time to go to vesa.


Cary

I'm afraid that won't help you, jaunty freeze for some people even in recoverymode (no videodrivers loaded).. 

Check [http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

---

### Post by register88 on 2009-05-11
How to reverse edgers intel driver to normal ubuntu intel driver.
I installed the edgers intel driver, but get the pool perforceman.

xserver-xorg-video-intel                   2:2.7.99.1+git20090510.8d272478-0ubuntu0sarvatt X.Org X server -- Intel i8xx, i9xx display driver

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main

I want to get back normal ubuntu karmic intel driver for X.
something like Xorg-intel-XXX-2.6.xxx

Sorry, my english, but please help, thank you.

---

### Post by mc4100 on 2009-05-11
> **portis said:**
> For me, the occasional freeze became extremely rare after I turned of compiz.
It's funny, I had to do the complete reverse; only with compiz is UXA stable for me (at least with the current crack!). Tried un-composited metacity and X crashed when I tried to move a window. 
Mind you, KMS is a no-go, now: hard lockups are almost certain in every session.
I'm glad Intel decided to drop EXA (and XAA, I think) though, as now all focus (developer's and user's) is on making UXA perform to the same standard, and on top, it was designed to give performance increases and decent graphics finally due to GEM.

---

### Post by scaine on 2009-05-11
UXA is pretty stable on both my Mac Mini and my Dell X300.  They both use GMA950's - my Tosh U400 uses a GMA4500 and it's unusable with UXA.

Performance wise, I haven't seen much difference, but I love UXA for its ability to run SecondLife, GoogleMaps, etc without having to turn off Compiz first.  Very slick.

---

### Post by Starks on 2009-05-11
UXA has stabilized considerably as of a few days ago. The latest commits fixed the issues that were causing most of the crashes.

---

### Post by Sarvatt on 2009-05-11
> **Starks said:**
> UXA has stabilized considerably as of a few days ago. The latest commits fixed the issues that were causing most of the crashes.

Yeah UXA is stable for me as of may 2nd when I upgraded -intel on xorg-edgers to the UXA only version, outside of a few specific pages causing X to hang when opened in firefox because of the huge pixmaps that I have never triggered unless it was on purpose. I have 2.7.1 which has the UXA fixes in it but still has EXA in this repo for now incase anyone wants them

[https://launchpad.net/~sarvatt/+archive/sarvatt-graphics](https://launchpad.net/~sarvatt/+archive/sarvatt-graphics)

---

### Post by jerrylamos on 2009-05-12
> **Sarvatt said:**
> Yeah UXA is stable for me as of may 2nd when I upgraded -intel on xorg-edgers to the UXA only version, outside of a few specific pages causing X to hang when opened in firefox because of the huge pixmaps that I have never triggered unless it was on purpose. I have 2.7.1 which has the UXA fixes in it but still has EXA in this repo for now incase anyone wants them

[https://launchpad.net/~sarvatt/+archive/sarvatt-graphics](https://launchpad.net/~sarvatt/+archive/sarvatt-graphics)

I get a hang every couple hours where everything locks up, power off time.  How would I tell if it could be "uxa" since that's all 2.7.0 has?

Thanks, Jerry

---

### Post by Sarvatt on 2009-05-13
If the mouse still moves, theres a high chance 2.7.1 will fix it for you. 2.7.0 doesn't just have UXA, the 2.7 branch still has EXA and everything in it.. xorg-edgers is tracking 2.7.99.1 which is pre-2.8.

---

### Post by pluckypigeon on 2009-05-21
I get the odd freeze which needs the power off switch. :)

Compiz always freezes my pc. (Since Intrepid) :) 

The font on everything gets garbled after about 15 mins of the pc being on, especially in Firefox, making it near to impossible to read. :)

In xorg I've enabled EXA and UXA and get the same problems with both. :)

Is UXA really enabled by default though?? (In xorg-edgers repo)

---

### Post by Kareeser on 2009-05-21
Good to hear... and I'm guessing UXA is still for the 9xx series?

So me and my piddly 4 year-old 855GM is out of luck, I'm guessing? I could give UXA a shot again, but last time I tried, the results were less than spectacular :)

Worth a shot.

In other news: How do I check whether I have EXA or UXA enabled? glxgears used to report 700fps with EXA, and now it reports 200fps after upgrading to the 2.6.30rc5 kernel. I don't know what may have happened in the interim with regard to xorg-edgers, since that PPA is enabled too :)

---

### Post by erkiha on 2009-05-22
erki@siil:~ $ cat /var/log/Xorg.0.log|grep -i uxa
 (--) intel(0): Using UXA for acceleration

---

### Post by biji on 2009-05-22
i'm using jaunty and latest X.. nice performance ^^ for better result try to install 2.6.30 from kernel mainline (but you have to compile restricted drivers yourself )

---

### Post by nanog on 2009-05-22
I'm running xorg edgers uxa on all my intel systems now. Intel performance was so bad using default jaunty that it was either that or downgrade to intrepid (it works if you hack dpkg manually).

I cannot bear to use my nvidia laptop now and its ugly, proprietary xorg.conf based mode changes. 

Xrandr and intel just works. 

Add 3 monitors...no problem. 
Resolution changes on the fly...no problem. 
Use an lcd projector (beamer) with borked edid...no problem.

---

### Post by Vaun on 2009-05-22
Dell Vostro A90 (Mini 9) upgraded kernel to 2.6.30rc6 using jaunty's proposed xorg-xserver-video-intel now I'm getting well over 750 fps in glxgears with Compiz running.  It was ~500 with Jaunty stock kernel. Not bad from this little machine ;)

---

### Post by psyke83 on 2009-05-22
> **Vaun said:**
> Dell Vostro A90 (Mini 9) upgraded kernel to 2.6.30rc6 using jaunty's proposed xorg-xserver-video-intel now I'm getting well over 750 fps in glxgears with Compiz running.  It was ~500 with Jaunty stock kernel. Not bad from this little machine ;)

It's unfortunate that glxgears performance means absolutely nothing, though.

---

### Post by Vaun on 2009-05-22
psyke83,

You're absolutely right.  Glxgears is not a great base for performance especially because all the 3D rendering modes are not even utilized.  My performance is exceptional using EXA with 2.6.30rc6 and the default intel drivers in jaunty-propsed.  I just had to rebuild my Broadcom wireless driver with module-assistant.

This is the best $199.00 I've spent in a long time.

---

### Post by jerrylamos on 2009-05-23
Performance measures....

I've been using gtkperf to track intel driver performance lately, just because it is on synaptic.  It seems to be at a more elemental difference than some of the fancy 3D stuff, but it sure does show up (some) Intel driver changes.  This 1 ghz i830 Celeron Thinkpad gets 49 seconds to run through the standard 100 repetitions, my 2 ghz Celeron i845 used to do it in 31 seconds however yesterday's update dropped to 27, my other Thinkpad 1.5 ghz Pentium with ATI gets 13 while my faster 3.3 ghz Celeron ATI gets about 9 or 10 depending on the latest updates.

Thinkpad 1.0 gHz Celeron i830_______49
Thinkpad 1.5 gHz Pentium ATI________13
ThinkCentre 2.0 gHz Celeron i845____27
Compaq Presario 3.3 gHz Celeron ATI__9 or 10

All these are using "uxa".  Intrepid without "uxa" definitely slower however I forget the numbers.

A good 3D demo is glxdragon which has 3D, perspective, highlights, shadows, hiding, ...  The strange thing to me is my best fastest smoothest video pc is miserably slow with it, to the point that it is extremely boring to run.  It has ATI Radeon graphics which are much much better than Intel on YouTube videos, even though the glxdragon performance sucks.

There's a bunch(!) of performance tests on Phronix however I haven't seen anyone recommend a reasonable subset that might show some useful video driver changes.

Oh, yes, glxgears on this Thinkpad screws up the display unless Option "Tiling" "false" is used, so glxgears to me has a functional purpose.

Jerry

---

### Post by Starks on 2009-05-23
KMS+UXA+DRI2 = No more tear-free playback

---

### Post by Starks on 2009-05-23
This bug is suggested reading.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/377090/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/377090/)
[RFC Karmic] DRI2 swapbuffers

---

### Post by nanog on 2009-05-27
```
"KMS+UXA+DRI2 = tear-free playback:
```

I confirm this in 768p and 1080p on 945GM!

---

### Post by Kareeser on 2009-05-27
Good to know that a Dell Mini 9 has better graphical capability than my laptop. :D

Last time I enabled UXA, Ubuntuforums would cause a system freeze. I may as well try it again, since it's been awhile.

How is xorg-edgers different from ubuntu-x-swat, may I ask?
Edit: Nevermind, answered my own question - ubuntu-x-swat is stable. Got it :)

---

