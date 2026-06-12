---
title: "Has anyone got knetworkmangler/KDE/wireless 4.2 to work"
date: 2009-02-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by caryb on 2009-02-17
As the topic says I cant for the life of me get it to work! I have come to the conclusion it's in there as decoration purposes only. I have a static entry in my interface file to get it to work but I have to edit it every time I go between work & home. Both sites use wep 128bit encryption.

Would love to hear if anyone uses knetworkmanager wireless working.


Cary

---

### Post by inportb on 2009-02-17
I used knetworkmanager before and it worked fine before I switched to using the network manager plasmoid.

But if you have a static entry, it would have to go; knetworkmanager does not manage static entries. But the plasmoid (maybe knetworkmanager too?) lets you set up profiles and stuff, so you could give it a try if you haven't.

---

### Post by PRGUY85 on 2009-02-17
I am loving the Network Manager plasmoid.  On latest updates I did, the wireless icon is finally showing.  Previously, I would be connected but it would show no icon.

---

### Post by W2IBC on 2009-02-17
> **PRGUY85 said:**
> I am loving the Network Manager plasmoid.  On latest updates I did, the wireless icon is finally showing.  Previously, I would be connected but it would show no icon.

same here. seems the updates have fixed alot of the issues i was having with it.

---

### Post by inportb on 2009-02-17
Yup... it still has overflow issues, though; it needs scrollbars.

---

### Post by quickshade on 2009-02-17
According to the developers it's still unfinished. It was suppose to launch with 4.2 but they never got it fully finished. So only half of it worked. It was pulled from KDE trunk and merge in with KDE 4.3. The program itself is now mostly done and is being merged back into KDE development, but needs more work and refinement before it can be used full time. The expected plan is to bug test it and get an early mostly complete version out to spring distros next month, while providing the final release in KDE 4.3 I know wireless was a big TODO on the list.

---

### Post by PRGUY85 on 2009-02-17
Offtopic: Where is my Gmail Plasmoid?

---

### Post by caryb on 2009-02-17
I have the plasmoid installed & it manages the eth0 with no problems but it wont connect to the wireless (with the interface file empty) it says enabled but not updated yet! I have the ssid & hex key info there.


Cary

---

### Post by quickshade on 2009-02-19
> **caryb said:**
> I have the plasmoid installed & it manages the eth0 with no problems but it wont connect to the wireless (with the interface file empty) it says enabled but not updated yet! I have the ssid & hex key info there.


Cary
Not sure if you saw my post, but it doesn't work yet. It's an early alpha- pre-beta at best, just merged into KDE-playground. The app is not yet finished or even stable enough for full time use, and Wireless is the number one thing that just doesn't work yet. Developers know about it and are working on it. But as I've said before don't expect anything stable until mid march or early april when they release an early version for the spring distros, After further testing and some minor tweaks the final version will ship with 4.3. If the spring distros pick it up they will most likely upgrade it from trunk before KDE 4.3 is released. So don't expect anything for another month or so, although it has become much more stable since the last release.

---

