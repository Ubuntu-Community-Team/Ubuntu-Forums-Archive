---
title: "Problem after upgrade from 10.04"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by DrScum on 2012-12-20
I just performed an upgrade from 10.04 LTS to 12.04 LTS using the update manager. The 10.04 system was up to date when I started. On 10.04 I was using docky and had a global menu bar.

 The upgrade went through without errors but after rebooting there is neither a unity menu bar nor a main menu bar. Additionally the window borders are gone.

How can I diagnose/fix this problem?

---

### Post by DrScum on 2012-12-21
There are some new facts that might help someone to give me a hint:
here the data I already mentioned in my first post a little more structured:
[LIST]
[LIST]
[/LIST]after upgrading to 12.04 I have a desktop with ONLY Docky to access applications
[*]there is no unity application bar to the left
[*]there is no main application bar on the top (which I had setup in 10.04)
[*]windows have no borders i.e. no buttons to minimize/maximize and close
[/LIST]
now the new data:
[LIST]
[*]when I open a terminal and enter "compiz --replace &" the the menue bar on the top appears to be there since when I click the mouse on the right, I get drop down menues from the network manager, the print manager, the clock and so on. But the bar remains invisible you can just see a black band the size of a menue bar. The same seems to happen for the unity application bar on the left. The desktop background is distorted with a line from top to bottom about where the right border of the application bar would be.
[/LIST]

Thus I think there is a problem with the compositing manager. What I would like to do at this point is to get rid of all "Gnome leftovers" from the old install and start with the unity desktop that came with the upgrade. I think I could handle it from there. Any help is appreciated since I am a sitting duck in the current situation.

---

### Post by fdrake on 2012-12-21
evrything you need to know is here. [http://www.liberiangeek.net/2012/03/return-to-gnome-classic-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/return-to-gnome-classic-in-ubuntu-12-04-precise-pangolin/)

---

### Post by DrScum on 2012-12-21
Thanks fdrake, that helped. I am close to a functional system now. Except the network setup causes trouble (see new post) [http://ubuntuforums.org/showthread.php?t=2096854](http://ubuntuforums.org/showthread.php?t=2096854)

---

