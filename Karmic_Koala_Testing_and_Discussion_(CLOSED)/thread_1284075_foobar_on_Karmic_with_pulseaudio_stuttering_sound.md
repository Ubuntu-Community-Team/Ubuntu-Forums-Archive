---
title: "foobar on Karmic with pulseaudio: stuttering sound"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ernstblaauw on 2009-10-06
Hi,

I have Karmic installed with the wine1.2 package from the repo's, which is wine 1.1.30. If I start foobar, I get really ugly stuttering sound.

According to [this post]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14597") on AppDB, I have to use padsp. That works indeed if no other program plays audio, so it's not a solution. 

Has anyone found a good solution for running foobar on Karmic with pulseaudio?

---

### Post by ernstblaauw on 2009-10-07
I solved it by compiling wine myself with the [WinePulse patches]("http://art.ified.ca/?page_id=40"). Now, foobar works great!

---

### Post by 1forthedoctor on 2009-10-15
there is a ppa with a patched wine here: [https://launchpad.net/~neil-aldur/+archive/ppa](https://launchpad.net/~neil-aldur/+archive/ppa)
it is pretty much up to date as well

---

### Post by janascii on 2009-10-28
A little thing I found out when trying to get this working.  I installed the repo and wine1.2 and couldn't get my audio to work without stuttering.  Turns out while looking at the package versions in Synaptic, that the karmic repository had 1.1.32-0ubuntu3 as a higher version than the 1.1.32-0ubuntu1+winepulse from the ppa.  I had to tell it to force the version in order to get the patched wine installed.

---

