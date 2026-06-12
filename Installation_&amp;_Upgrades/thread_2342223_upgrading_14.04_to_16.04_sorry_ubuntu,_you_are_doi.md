---
title: "upgrading 14.04 to 16.04: sorry ubuntu, you are doing something wrong."
date: 2016-11-04
forum: Installation &amp; Upgrades
---

### Post by b.d.n on 2016-11-04
I'm ubuntu user since 7.04 or earlier (could not find the first install disc). 
By every upgrade there was some issue: I've coped with it, more take it than leave it - because, in my world, it was worth it.
As Unity sucks I've allowed me Ubuntu-Gnome (3)- but still, Ubuntu!
Now I had perfectly functioning 14.04 on my - in between upgraded to Haswell and SDD - system, but it barfed: no updates more. 
So I upgraded to 16.04.
It shoot out my data disc. Ok, few days later I've got it online again. Could have been anything.
But the boot time escalated from some 10 seconds to minutes(dmsg):
```
[    2.639532] clocksource: Switched to clocksource tsc
[   91.215098] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
```
Did fsck.ext4 -cDfty -C 0 on /dev/sda1 of course.
So I went to Google to find the culprit, business as usual.
Not much to find. Found issues inconclusive: seems to be problem that comes and goes in many disguises. No ultimate solution: I've tried most of them.
I've had already similar Ubuntu upgrades issues on my laptop and nettop: crush by copy/paste in terminal, no graphical login possible - but there, having /home on separate partition, I migrateted to Arch. See there, no problems!
 Installing Arch is major PITA, because you have to know what you want to have - which is not so obvious when you start. And the pacman is an Alien. But, after all is is done, it works as expected (so far) .
Well. I've backed up my /home on my main system. 
Do you guys have some tip for me?  
Or is Ubuntu a past time for me?

---

### Post by kevdog on 2016-11-04
Other than just a rant -- you'd have to give some useful information if you really need help.  What you've posted doesn't help anyone.

---

### Post by alexjpowell on 2016-11-05
Just mount /home on another partition, write a list of your programs and do a fresh install

---

