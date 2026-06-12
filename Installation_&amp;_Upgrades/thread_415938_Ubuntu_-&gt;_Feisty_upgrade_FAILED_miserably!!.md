---
title: "Ubuntu -&gt; Feisty upgrade FAILED miserably!!"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by CaptSaltyJack on 2007-04-20
Got a fatal error:

Could not install '/var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb'

2007-04-20 18:11:15,759 ERROR got an error from dpkg for pkg: '/var/cache/apt/ar
chives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb': 'subprocess pre-ins
tallation script returned error exit status 2

And it looks like the upgrade is continuing.. though I got a warning that my system might be in an unstable state.  Great, thanks.

---

### Post by CaptSaltyJack on 2007-04-20
Wow.  WOW.  OK, so the update manager just closed for some reason.. no explanation, no error, nothing.  Just.. gone.  The logs in /var/log/dist-upgrade show nothing relevant.  Now I'm going to have to reboot and cross my fingers, but not before I tar up my important stuff.

The sucky part is, I spent hours customizing this system with icons, Beryl, gdesklets, all kinds of visual changes.. now if I reformat, those will all be gone.  Ugh.  I guess this is partially my fault, I should've waited a few weeks for all the bugs to get ironed out.  That'll show me.

Ubuntu team: dudes.. next time, before you release the next version (whatever it's going to be, Grumpy Gator, Groovy Gazelle), test that upgrade script on SEVERAL different Feisty boxes that are highly customized, to make sure it doesn't break stuff.  Geez.  I'm rather disappointed.

---

