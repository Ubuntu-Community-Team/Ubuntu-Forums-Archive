---
title: "Blank screen when booting up: Kubuntu KDE 4"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by Dekkon on 2008-02-12
When I boot up into the live cd, everything seems to be fine. Then the screen turns blank, I tried to use the CTRL + ALT + F1 and sometimes that works and doesn't work. 

I usally log onto the ubuntu username and try issuing the command "startx" but that gives me alot of fundy crap, and I try to issue the command "startkde" but that gives me some more crap. I also don't really want to install kde 4 from a original kubuntu installation because I get alot of extra crap I don't want along with kde 3 apps. 

The live cd used to work, but now I really don't know what happened. 

Thanks for assisting with my problems.

---

### Post by trippinnik on 2008-02-13
Originally there was a problem with kdm-kde4.  You can either do 
```
sudo dpkg-reconfigure kdm-kde4
```
and choose kdm or gdm (if installed)
or
try an ```
aptitude dist-upgrade
```

---

