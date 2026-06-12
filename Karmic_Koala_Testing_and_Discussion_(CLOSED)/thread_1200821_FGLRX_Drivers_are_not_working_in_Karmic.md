---
title: "FGLRX Drivers are not working in Karmic"
date: 2009-06-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jfanaian on 2009-06-30
I wanted to post a notice regarding the fglrx drivers in Karmic. Due to an update on Xorg in the current alpha, the ATI drivers will not work until ATI provides an update.

The current version of Xorg in Karmic is 1.6.1.901 (1.6.2 RC 1). In my Xorg.0.log I find an error from fglrx asking for the 1.4.1 version "driver needs X.org 1.4.x.y with x.y >= 99.906". As far as I know, we have to wait until ATI releases an update built for the current version of Xorg.

Please correct me if I have provided any incorrect information.

---

### Post by descendent87 on 2009-06-30
the newest fglrx driver only works with 2.6.28 kernel aswell, and karmic is currently on 2.6.30/2.6.31 RC1
ATI drivers are a joke, I'm just going without 3D until the opensource radeon driver has it for my card

---

### Post by Threedays on 2009-07-04
Agree, it's pretty annoying.  I love ATI hardware, but their driver support in Linux is woeful.  I may have to shift to Nvidia on the next upgrade in a year or so, so lets hope they get their act together on the fastest moving OS.

I like how they have made the drivers open source, so maybe there will be progress.  Also remember that they usually release drivers once a month.  Any day now for new driver.

---

### Post by descendent87 on 2009-07-04
> **Threedays said:**
> Agree, it's pretty annoying.  I love ATI hardware, but their driver support in Linux is woeful.  I may have to shift to Nvidia on the next upgrade in a year or so, so lets hope they get their act together on the fastest moving OS.

I like how they have made the drivers open source, so maybe there will be progress.  Also remember that they usually release drivers once a month.  Any day now for new driver.

what card do you have? Open source drivers have working 3D for all cards upto r5xx, r6xx-r7xx 3D will hopefully be finished by end of summer (would be great if they were finished before karmic is released)

---

### Post by Dimarchi on 2009-07-06
I expect there will be a Karmic specific FGLRX driver *after* Karmic is released, or slightly before that, if the Jaunty experience is of any indication. As descendent87 points out, the open source drivers are progressing along. Phoronix is a good site for this kind of information (if you wish to follow it), since the "Popular In The Forums" box in the front page frequently lists ATI driver related stuff - both FGLRX and open source, among other Linux related forum discussion threads.

---

