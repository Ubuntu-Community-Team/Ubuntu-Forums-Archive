---
title: "Xorg upgrade confusion"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by fhco on 2007-06-30
So after switching to Feisty, I see this in the update manager:

[img]http://jaredbarker.googlepages.com/xorg.png[/img]

I didn't activate this upgrade initially when I moved to Feisty, but I know that at one point the option was not greyed out. As it stands, it will not let me check it to upgrade, not even if I sudo update-manager. I'm sure I'm missing something obvious, but I just can't figure out how why the option is greyed out and why I can't do the upgrade. Any advice?


edit: switched image to my hosting, didnt know waffleimages was blocked

---

### Post by Gremlinzzz on 2007-07-01
that command fixs my resolution which is 1440 x 900 but it doesn't work for everyone some say it screwed up there computers resolution.
    * Another way to get the resolution you want is to do this(doesn't always work): 

sudo apt-get install xserver-xorg-video-intel
this is the way it reads in the ubuntu guide--- if your resolution is right you dont need it.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

