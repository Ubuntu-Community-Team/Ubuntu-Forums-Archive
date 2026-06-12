---
title: "After Install, Blank Screen"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by ScoobyDan on 2005-08-09
Hello All,

I want to try Ubuntu as my first Linux distro, as I am gettign fed up with WinXP crashes and issues.

I have installed Ubuntu on a spare drive I have, but once it goes through the first reboot, all of the text is displayed, then the screen goes blank and I get an "Input out of range" error message from my monitor.

If I boot into "Safe Mode" (can't remember the exact term ;) ), Ubuntu boots to a command prompt, but I have no idea what to do from there.

I have tried a live CD as well as an install CD, with the same results.

Here is my spec:

AMD Athlon 1800+
ASUS A7A266-E
512MB RAM
NVIDIA GeForce 2 Ti
SoundBlaster Audigy
DVD-RW
3 x HDD

USB Modem - being replaced with a router in a couple of days :D

Any bright ideas?

Many thanks

Daniel

---

### Post by Worzel on 2005-08-09
Might be some help here - under Hardware there's stuff about nvidia installs.

[http://kudos.berlios.de/kf/kf.html](http://kudos.berlios.de/kf/kf.html)

Jim

---

### Post by ScoobyDan on 2005-08-19
[QUOTE=Worzel]Might be some help here - under Hardware there's stuff about nvidia installs.

[http://kudos.berlios.de/kf/kf.html](http://kudos.berlios.de/kf/kf.html)

Jim[/QUOTE]
 Worzel,

Thanks for your help...

It turns out that

```

dpkg-reconfigure xserver-xorg

```

was not running automatically, so the default monitor and graphics card drivers were being used. I booted into recovery mode, ran the above and then selected the correct refresh rate for my monitor (thanks Google! :D).

I cannot tell you how much of a sense of accomplishment I got when I saw the login screen. I have never been so happy to see a brown desktop ;)

Daniel

---

