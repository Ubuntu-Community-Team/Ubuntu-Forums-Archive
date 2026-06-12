---
title: "Reinstalling from scratch"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by Zalbor on 2006-09-26
I imagine that Edgy will be released in the next month, or maybe a couple of months later. Currently I'm using Dapper which has been upgraded from Breezy.
I've heard that "upgraded" Ubuntu isn't as stable as when it's been installed in a clear partition, and I imagine that if I upgrade an upgraded one it will be even worse... So I'm thinking of installing from scratch when Edgy is released.
But the problem (and the reason I chose to upgrade last time) is that if I reinstall I'll need to install all the packages I'm using all over again. /home is in a different partition so my personal files and settings aren't a problem, but is there an easy way to "note" which packages have been installed and have them installed again after the root partition is formatted?
I realise it's a bit early to be asking this :p

---

### Post by jimbren on 2006-09-26
I don't know of an automated way to list out what is installed that would really be helpful. I suppose you could really basically do it by piping the output of an ls to a text file and going from there, but that would give you lots of information you don't need\want, and you'd probably end  up missing things anyway.
Something like:
```
ls /usr/bin > installed_apps.txt
```
and change the directories as you need to.

Personally, I just go through my program menu and take note of the important stuff I need, then go from there. 

Take a backup of your /home partition just in case you decide to smoke some crack during the installation and screw up your partitions or something--it could happen. Crack is tempting.

Doing a fresh install with /home left in tact is so incredibly nice...you get a shiny new installation and you have all of your data intact...instead of restoring your backups, you get to poke around and look at your new toys.  

I like it.

jim.

---

### Post by orb9220 on 2006-09-26
[http://www.arsgeek.com/?p=564](http://www.arsgeek.com/?p=564)
Ubuntu Tricks - how to generate a list of installed packages and use it to reinstall packages

---

### Post by Zalbor on 2006-09-26
Thanks! That will come in handy to be sure. ;)

---

### Post by Zalbor on 2006-09-27
Hm... If however the new release uses a package with a different name, and the one with the old name doesn't exist (or worse, conflicts with the new one) will doing that cause a problem?

---

