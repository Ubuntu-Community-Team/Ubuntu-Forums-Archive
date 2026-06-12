---
title: "Ubuntu lucid doesn't show panels on startup"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by lone_wolf45 on 2010-05-20
My problem is many folds, as i went tweaking with things that were probably better left untouched. 

I have a computer with pentium 3 that i'd like to run ubuntu 10.04 on. I've installed it from a livecd (the cd is fine, because i used that cd to install 10.04 on another machine, and its working perfectly). The installation went fine, and on the first boot everything worked fine as well. but when i tried it again, the computer started but at the desktop there were no panels on the top or bottom, although every thing else was working. 

I could use Alt+F2 to run any application that comes preinstalled on the ubuntu cd including the terminal, but i can't access Applications, Places, System, etc. 

Everytime at startup during boot there is a message that prints "error: no suitable mode found" "error :unknown command 'terminal'" (without the quotes). 

this computer has a bit of a history as i once tried to install linux mint on it but failed because of a bad livecd. the grub got installed wrongly,  tried to reinstall xp, didn't work, then ultimately after trying a few other things turned to DBAN, which surprisingly also failed crashing everytime i ran it before completing its erase, which leads me to believe that Dban didn't leave my hard drives in too good a condition. when the ubuntu live cd worked however i was ignited with a brand new spark of hope, and even that now is starting to diminish, is there no hope for my pentium 3...

if the above information was not helpful please direct me on how i can provide the correct information. Will be very grateful for any suggestions.

---

### Post by SlidingHorn on 2010-05-20
In your terminal, run:

```
gnome-panel
```

Save your session & restart

---

