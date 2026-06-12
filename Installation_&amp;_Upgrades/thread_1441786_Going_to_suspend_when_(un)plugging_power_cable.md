---
title: "Going to suspend when (un)plugging power cable"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Sly1972 on 2010-03-29
Hi,
 
Something weird happens on my Fujitsu-Siemens Amilo 7310 laptop ([http://ts.fujitsu.com/Resources/158/1745916639.pdf](http://ts.fujitsu.com/Resources/158/1745916639.pdf)).
 
When I unplug or replug the power cable, the system goes automatically in suspend mode, without anything I can do. Even weirder, it does not resume from suspend when I click on the power button: the screen seems to light up, but stays blank, no activity whatsoever on the hard drive. I have to force switch off, then back on to use my laptop.
 
Now this is recent occurence and may be linked to one of the packages I have activated/installed when trying to solve my other problem ([http://ubuntuforums.org/showthread.php?t=1440484](http://ubuntuforums.org/showthread.php?t=1440484)).
 
Can someone tell me how I could identify the module that is causing this problem? Or tell me what I did wrong altogether?
 
Thanks for any help.

---

### Post by wombuntu on 2010-04-01
Yep, I think this is a known bug that affects a few people. (I have it myself).  I have been looking around for some info (am new to the joys of linux) - but have not missed anything from my old xp system (except battery life - but I am still looking into that).

anyway, this link (I think) - [https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-power-manager/+bug/425411](https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-power-manager/+bug/425411) has some details on it.

I think a fix has been nominated for release, but am still looking to confirm.

Side Note - here is a short thread that may give you a temporary workaround....
[http://ubuntuforums.org/showthread.php?t=1278765](http://ubuntuforums.org/showthread.php?t=1278765)

hope this helps.

---

### Post by Sly1972 on 2010-06-20
Problem seems to have been solved in Lucid (10.04)

---

