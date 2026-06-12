---
title: "Repository mirrors for ubuntu 9.04"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by G4G4N on 2011-04-03
Hello everyone. 
I am using ubuntu 9.04 (i've not upgraded for some reasons). As we all know the canonical does not support repositories of ubuntu 9.04 any more. So i can't get anything from there.
This is really freaky. 

Is there something like repository mirrors for ubuntu 9.04, which are still alive.?

---

### Post by mörgæs on 2011-04-04
Are you aware that you system has not received security fixes for half a year?

---

### Post by Frogs Hair on 2011-04-04
I checked at the link and 9.04 is no longer on the list. [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by ~Plue on 2011-04-04
> **G4G4N said:**
> 
As we all  know the canonical does not support repositories of ubuntu 9.04 any  more. So i can't get anything from there.

try replacing *[COLOR=DimGray]archive.ubuntu.com[/COLOR]  *with*  [COLOR=DimGray]old-releases.ubuntu.com[/COLOR]* in your sources.list

---

### Post by santorini on 2011-10-22
I tried ~Plue's suggestion and it seems to work!

I have a old ATI Xpress 200m chipset and I want to use ATI proprietary driver 9.3 (later releases do not support this chipset anymore). And after Jackalope, newer releases use an updated version of xorg-server which the proprietary driver cannot work with...

I think many people with this chipset has the same problem...

---

### Post by imnotrich on 2012-04-10
> **santorini said:**
> I tried ~Plue's suggestion and it seems to work!

I have a old ATI Xpress 200m chipset and I want to use ATI proprietary driver 9.3 (later releases do not support this chipset anymore). And after Jackalope, newer releases use an updated version of xorg-server which the proprietary driver cannot work with...

I think many people with this chipset has the same problem...

My ML-3109 Gateway laptop has this ATI Radeon Express 200m as well, seems to work ok with the generic driver supplied by version 9.04 but I am unable to install the ATI driver (epic fail) and Jaunty 9.04 is the last Ubuntu version that supports my very common, recent vintage Realtek 8185 wifi. I'd love to upgrade to a more current version of Ubuntu (since buying a new laptop every few months is out of the question) But...Ubuntu seems to have abandoned me.

---

### Post by mörgæs on 2012-04-11
You could try a fresh install of 11.10 using wired internet access and post a question in the network forum, when you want to install the wirefree card. As seen here

[http://ubuntuforums.org/showthread.php?t=1941205](http://ubuntuforums.org/showthread.php?t=1941205)
[http://ubuntuforums.org/showthread.php?t=1514691](http://ubuntuforums.org/showthread.php?t=1514691)

the card does indeed work for version after 9.04.


Why do you want closed-source drivers for the graphics card?

---

