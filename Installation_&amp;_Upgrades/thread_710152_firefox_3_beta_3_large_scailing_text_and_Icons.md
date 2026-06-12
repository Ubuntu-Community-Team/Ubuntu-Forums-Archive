---
title: "firefox 3 beta 3 large scailing text and Icons"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by tzury on 2008-02-28
I installed firefox 3 beta 3 and have experienced a weird and large appearance of the GUI.
THe toolbars are all scaled up as well as the Icons. All logos and images are pixelized.

Attaching an image which shows version 2 and version 3 side by side
Anybody experienced this, and solved it somehow?


(BTW: the windows version works fine)


[IMG]http://afro.systems.googlepages.com/ff2n3.png[/IMG]

---

### Post by Oxygene on 2008-03-09
I've got firefox 3 beta 3 running for a while now and suddenly, today I've got the same problem.  Everything is rendered doubled in size (except text in the GUI which just has the double padding).

I've already tried to remove and reinstall firefox through apt-get, but to no avail.

Any ideas?

---

### Post by jannroger on 2008-03-10
Hi, I have the same problem. I have a screen res on 1920x1200 if I scale down to 1024x768 the UI of firefox gets resized to be correct.. But when I scale up to my "normal" res, it goes back to the large UI..

---

### Post by jannroger on 2008-03-10
well, have you seen... Some config tweeking made my day..!!!

In order to fix it: at address line go to *[COLOR="Red"]about:config[/COLOR]* and set *[COLOR="Red"]layout.css.dpi[/COLOR]* to *[COLOR="Red"]96[/COLOR].*

---

### Post by Oxygene on 2008-03-10
Funny enough I've just recently bought a new monitor (1920x1200).  So there we have a common config.

Now I'm wondering if this is a bug or a feature?

---

### Post by fozzieb on 2008-03-11
Nice one, sorted

---

### Post by Cherry Cotton on 2008-03-11
I had the same problem, just now. It freaked me out!

The "about:config" trick fixed it. Wow, thanks!

---

