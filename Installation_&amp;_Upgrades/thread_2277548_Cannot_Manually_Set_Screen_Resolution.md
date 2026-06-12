---
title: "Cannot Manually Set Screen Resolution"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by typos1 on 2015-05-09
just trying to set up my new pc, its got a Radeon 6520g APU, the picture is rubbish using the proprietary drivers, its much better with the open source drivers, but I only get one resolution available and its the wrong one - I get a black border round the screen. the monitor is 1920x1080 capable but the only res allowed in screen display is 1400x1050 4:3. 

I get a message "failed to get size of gamma for output default", when I try to change it, can anyone help ? Thanks

---

### Post by typos1 on 2015-05-09
When I try and edit my Xorg conf file it says I m using the proprietary  driver, but I m not !

It also says the resolution is 1920x1080 (the  monitor IS) but the open source drivers dont go any higher than 1400x1050 at 4:3.

---

### Post by alex375 on 2015-05-09
use nvidia-settings

---

### Post by QIII on 2015-05-09
> **alex375 said:**
> use nvidia-settings

Probably not helpful with an AMD GPU.

@typos1 -  how did you install the drive?

What is the output of

```
 fglrxinfo 
```

---

### Post by typos1 on 2015-05-09
Its the default open source driver that installed with ubuntu. I ve played around with the proproietary drivers some more now and I ve got a much better picture. Though I dd still like to try the open source ones at the correct resolutio.

---

### Post by typos1 on 2015-05-10
Actually no, I played around with the settings in Catayst - the app that installs with the proprietary drivers, for ages and thought I d got a better picture, but I must have just got used to it, because when I switch back to my old pc (the one listed in my profile) the picture is a world away, its amazingly better than the 6520G and I m just talking about the way it renders the desktop, not gaming or anything.

---

