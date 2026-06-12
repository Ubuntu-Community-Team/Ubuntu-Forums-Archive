---
title: "GUI problem after install"
date: 2004-12-02
forum: Installation &amp; Upgrades
---

### Post by scanlanlee on 2004-12-02
Hi all,

I am having a small problem when installing Ubntu - this is being done on Virtual PC on a XP system.
Problem is that setting the res to 800x600 or 1024x768 on install makes no odds - when Ubuntu boots for the first time.
The system drops in a res of 1600x600?? Has anyone any ideas why this is or how to fix it.
I have 2 installs one with web updates and one without and they both do it.

Any ideas?

---

### Post by boytie on 2004-12-04
Your problem should come from the fact that Virtual PC supports only 1, 2, 4, 8, 16 or 32 bits for colour resolution.
Ubuntu probably detected 24 bits during setup, so it doesn't work.
I'm afraid I dont'know how to change this behaviour during setup.

Anybody whishing to add more on this?


Boytie

---

### Post by boytie on 2004-12-04
Actually, I just tested it on Virtual PC and had the same behaviour.

Just login in recovery console and reconfig xserver using
sudo dpkg-reconfigure xserver-xfree86


Boytie

---

### Post by scanlanlee on 2004-12-07
Cheers, 

Will try that this evening

---

### Post by scanlanlee on 2004-12-07
Spot on advice - I am logged in and using Ubuntu as we speak.

Thanks again for your help

 :-D

---

