---
title: "broken gnome after upgrade"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TVAbuntu on 2008-10-23
I upgraded today via update manager, and on reboot gnome wouldn't start after gdm login ("brown screen of death"). Tried CD, same result. Sometimes I would get a black screen. Both times with a mouse pointer, but nothing else. Cannot get back to a shell at all from that point. I tried a reconfiguring xorg.conf etc, uninstalling/reinstalling both x and gnome (from terminal--the only login that worked, even rescue gnome session had the same result as above) with no luck. Finally installed Fluxbox (which took all of 60 seconds!!) and it works fine, which leads me to believe it's a gnome problem not an xorg problem. 
On the downside, I would like to use gnome, and I can't figure out why it's not working (ideas??)
On the plus side, fluxbox (and Opera) is really fast with this system, and it's all a learning experience. My stable box is sticking with Hardy for while, running great.

System: Dell 4300s with standard intel P4 2gHz, 750 RAM, Intel VGA  82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics, Realtek ethernet

---

### Post by TVAbuntu on 2008-10-23
After some more research, this is a reported bug (launchpad 259385) related to compiz. 
Workaround is to 
sudo aptitude remove compiz compiz-core

SOLVED

---

