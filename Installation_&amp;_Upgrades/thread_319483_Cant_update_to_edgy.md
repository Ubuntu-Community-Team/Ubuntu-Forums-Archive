---
title: "Cant update to edgy"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by BatteryCell on 2006-12-15
Ok, the gods must be against me or something...Yesterday I decided to upgrade to edgy, so I follow the instructions provided on the kubuntu website (apt-get method) and everything is holly jolly till a warning comes up saying that I have to remove stuff from /usr/X11R6/bin and the upgrade is going to fail.  Ok so I follow the directions and remove all the stuff from X11R6 (old ati drivers that I dont need any more cause I have nvidia) and try the method again.  Well, I guess that I wasn't sposed to do that cause it yelled at me about broken packages and suggested that I fix it with dpkg -f install, which proceeds to fail.  At this point I am pissed as anything and just want my comp back, so I go, switch the repositories back to dapper and re-do the entire thing, however every time that I try to upgrade it tells me to fix broken packages with dpkg -f install...which doesnt work....so I try to use synaptic to fix it and it starts throwing me errors...so I do "Fix Broken Packages" and it removes xserver-xorg-core.....but its the only thing that I could see working so I do it; as expected x dies.  Ok so now Im in terminal and trying to get my x back...yea xservers gone...eveyrthing graphical is gone, kde, gnome, xserver, xorg, nvidia, everything....so I install them and reboot the system (after like 1 hr) by now im seething...lol...neways xserver of course fails again, I go back and do a dpkg-reconfigure xserver-xorg...select the vesa driver..and x boots.  Ok, now kde is the ugliest god darn thing I've ever seen...some fonts are half the size of the screen, some arent, there is no taskbar, no kmenu, its just wonderfull...Ok so I go to synaptic to get some of my old packages back, you know like amarok and screensavers and such...spend about 1hr redoing everything so that it looks ok again.  And now I start getting locale errors...I try the locale command, it throws errors, I try to export the locals, that still gives me errors...its 2 in the morning by this point so I give up and go to bed.  Oh what tomorro holds...so I get home and start fixing up the system, about an hour and 5 reboots later kde is kinda functioning like it used to.  Of course gtk is in the crapper for some reason and im still getting locale errors, so i figure "you know what, my systems already screwed I might as well just try to upgrade the system again with synaptic this time"...yea apparently I took a stupid pill this morning...now once again I am mid-updated, meaning that everything is fricken broken all because firefox is now giving me troubles:
```
E: /var/cache/apt/archives/firefox-dev_2.0+0dfsg-0ubuntu3_amd64.deb: trying to overwrite `/usr/lib/firefox/regxpcom', which is also in package firefox

```
pops up now and the whole upgrade fails, I cant fix the packages, I dont want to go through another reinstall cycle...if anyone can tell me what is wrong with my computer it would be greatly appreciated

---

### Post by bulldog on 2006-12-15
You probably don't want to read this...........but a clean install from a cd-rom was quicker.:D

---

### Post by BatteryCell on 2006-12-16
Lol good point, lucky for me I just installed the update manager and did it that way, still getting errors but at least its edgy...lol..darnit now my printers broken ... thanks for the tip though, when i up again i might just do that instead :D

---

