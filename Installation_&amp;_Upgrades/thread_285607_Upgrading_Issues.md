---
title: "Upgrading Issues"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Silver Comet on 2006-10-27
Well I decided to do the upgrade tonight to edgy with my laptop. (family has been using my desktop to follow the progress for a while and it has some cool stuff for laptops).

Anyway, all fine, got to a point where it asked me what to do about files (can't remember the file). and then the update hung, and passwords wouldn't accept my usual one. so I had to restart, a bit slow, and the progress bar appeared grey (thought it was orange, with a colour logo, mines all silver and pixilated :S).

Got in, ran upgrade with 
```
sudo gksu "update-manager -c"
```
and then
```
gksu "update-manager -c"
```
as the wiki said, but there are four items "held back"
```
ben@kharn:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  gkrellm libggi2 libsdl-ruby1.8 mplayer
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
ben@kharn:~$ 
```

so, apt-get and upgrade didn't fix that, then i noticed another strange bug, my mouse (touchpad) keeps freezing for a minute, until I leave it alone, this can make navigating very difficult, anyone can think of a fix for that would be excellent.

So to clarify:
mouse is freezing, for a minute
art seems to be displaying wrong.
updates not working, but greyed out in upgrade manager &
apt-get upgrade-dist returning all fine except 4 hung back.
things seem to be running slightly slower. (like a little bit of lag between menus that wasn't there before, but that's just an example, it can be very slow =/)

---

