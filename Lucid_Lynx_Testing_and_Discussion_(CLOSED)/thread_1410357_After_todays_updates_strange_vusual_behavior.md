---
title: "After todays updates strange vusual behavior"
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-02-18
Just after installing todays , Feb 18th daily and updating I get a strange behaviors when using the games.

Open Games, AilseRiot, Klondike. When you drag a card from one area to another the card your dragging smears or has a "trail". This hasn't happened until today. I have two installs the the previous install isn't effected.

I'm using on both installs, Theme = human, visual effects = normal. Even if I turn off any visual effects, it does the same thing.

Anyone else with this behavior?

---

### Post by cariboo on 2010-02-18
I get the same thing running Lucid in a VM. I haven't changed the default theme, or added anything but conky to the desktop.

---

### Post by dondiego2 on 2010-02-18
I just finished my update and no problems here.

---

### Post by godhika on 2010-02-18
Just a guess. maybe the css-window decoration patches that landed today in gtk? Hamster panel-applet for example now a window decoration which it hadn't before.

---

### Post by VMC on 2010-02-18
One thing I forgot. You need to go maximum to see the "trail" that the card you move leaves. Move it fast and the "trail" should appear. This is from a normal first install. I did nothing else.

---

### Post by psyke83 on 2010-02-18
With the latest updates I'm noticing this problem, and also stuttering with video playback (seems to skip every 1/2 second). I'm not sure if the video playback issue is related to the client-side windows patch, or if it's due to an unrelated update...

---

### Post by psyke83 on 2010-02-18
A bug has been filed: [#523949]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/523949")

---

### Post by VMC on 2010-02-18
> **psyke83 said:**
> A bug has been filed: [#523949]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/523949")

I noticed this is for Rhythmbox which right now is playing perfectly.

How do you thing there related - The video "trails" on the games?

Edit: after reading the bug report and opening Rhythmbox, the cpu went from 5% when minimized,  to 66% when opened. My music isn't stuttering though.

---

### Post by VMC on 2010-02-23
I'm marking this topic solved, since **gtk+2.0 (2.19.5-1ubuntu5)** has fixed my original issue.

---

