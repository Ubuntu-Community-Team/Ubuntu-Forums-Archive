---
title: "nvidia version 96 =&gt; black screen after x splash"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by it.henrik on 2009-10-21
Im using nvidia gforce 440 2 go with nvidia version 96 which gives a black screen on boot, again *sigh*. 

I use the "Hardware Drivers" tool to enable the driver and reboot when asked to. After watching the beauty of the x splash I end up with a black screen... feels so familiar.

Only way to boot into gnome is to either remove the /etc/X11/xorg.conf or change the "nvidia" module to "nv" and reboot.

How can I get ubuntu to boot into 9.10 with my nvidia card?

Every time I try to upgrade one version of ubuntu to a new version I have to spend hours and hours just to get into graphical user environment, its fricking frustrating! I have no idea on how many bug reports I have written, confirmed or verified regarding this but every time there is a new release Ubuntu manage to break a such basic thing like making use of a very old nvidia card which tons of other distros can handle. 

I have been a strong promoter of Ubuntu and trying to push it as much as I could but things like this are starting to make me give up, where did I put my windows XP pro CD... Getting X to run on my nvidia card worked out of the box on other distros many many years ago but has never ever work on a new release of Ubuntu.  

Yes Karmic Koala is beta but come on .. this card is maybe 9 years old and the possible solutions on how to get it to work have been posted in these forums and as bug reports so many times. If we want users to make the switch they have to be able to see something when the machine has booted!

---

### Post by DanaG on 2009-10-21
Unfortunately, on GeForce4 MX, I believe the nvidia drivers have been just plain broken for ages.... and by "for ages", I mean, even as far back as Intrepid's released version!  I get a segfault in nvidia_drv.so any time compiz or gnome-panel tries to load.  The only workaround was to disable composite; I said "screw that", and switched that system to using nouveau (using instructions from the wiki: [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/) ).

---

### Post by edin9 on 2009-10-21
Maybe it's time to buy a slightly better card? That thing must be really slow on GNOME or KDE.

---

### Post by it.henrik on 2009-10-22
It works just fine with nv, just no fancy pancy effects and I cant play games, movies or such. Why spend money on new hw when I can run Ubuntu and get all my email and web-stuff done on my 9 year old laptop.

I had 3D and used tv-out etc but every distribution upgrade of ubuntu puts me back on square 1 with a black screen to stare at.

---

