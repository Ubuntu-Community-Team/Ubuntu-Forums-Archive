---
title: "/dev/input/mice not created - what package to re-install."
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by metoo on 2005-11-07
Hi,

on a machine (i386) which I try to upgrade from debian sid to breezy (yeah, don't! It's not mine and I wanted to spare the personal re-configuration...) the device /dev/input/mice is not created and therefore the xserver dies.

I'm currently using /dev/.static/dev/input/mice and it's working, but that's not the way it should be.

lsusb sees the mouse (and gives full name).

I have already re-installed udev, hal, discover, libdiscover, hotplug and at one time during my tries the devices in /dev/input were created, but lost after the next re-boot. -event0 is all that is in there.

Anybody any idea which package is resposible for creating /dev/input/mice? Maybe I should delete some scripts before re-installing this? Just udev?

---

### Post by mlomker on 2005-11-07
udev creates all of those devices during startup.  A fresh reinstall would be the easiest fix, I think.  You could find more ongoing problems later...I had a variety of issues from Hoary -> Breezy, so Debian -> Breezy is not something that I'd expect to work out.

---

### Post by metoo on 2005-11-08
Thanks mlomker,

I guess, I will dive into the package, delete all the scripts manually and then re-install it. Could be other base scripts as well, as the default route is not set automatically, too.

I knew, that it would be risky. A new install is no option. I can only access the machine a few hours on the weekend. (That's why I cannot report any results for some time).

I read a lot about re-installation/new installation. This is totally OK, if switching distros. So in this case (debian to kubuntu) no question: my bad.
But from hoary to breezy or breezy to drapper, this must work without problems. SuSE did this since 5.3, 9 years ago. We are talking Linux, not Windows. So the question will be answered in April 06, when updating from breezy to drapper...

For the meantime, I will keep my sisters PC on debian sid. Will be interesting to see, how it handles the gcc transition, it's still on a Jan 05. state. I had planned to transfer it to kubuntu, but I'm not overly impressed now.

Installing the base system should give you a clean base system. I used a kubuntu CD to install into the debian partition. So there was no system running locking anything. The installer could change/adjust whatever it wanted to do.

But thanks anyway.
I will post an update, if I come around this. Otherwise, /dev/.static./dev... will stay there forever and for the route, I will hack a personal init.d script.
(SuSE once provided a rc.local file already implemented into the system for personal things. Ahhh, the good old days!)

---

### Post by mlomker on 2005-11-08
> But from hoary to breezy or breezy to drapper, this must work without problems. 

I was running amd64 during the last upgrade and it's always been a few steps behind i386 in refinement.  I didn't have any trouble with an i386 server upgrade.

---

