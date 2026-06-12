---
title: "Is there a way?"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by MarkLori on 2006-02-24
I am downloading Breezy right now and hope to do an install of XUbuntu then run Automatix and have almost everything done that easily. (At least as far as packages I use regualary)  Here on the work machine that will not be a problem as I have a T1 to play on.

The problem is that I want to do the same thing for the home machine.  Is there a way to save all of the debs used to build the system up here, then take them home and somehow make a local repository on the home system?  I have no internet connection on that machine at home.  I could hook it to a dialup, but that is truly painful and unreliable.  (My high end speed used to be about 21.6)  

Thanks for the help.  After using Linux for about 6 years now I have found Ubuntu to be great and the community support beats what some other distro's charge for!

Mark

---

### Post by cstudent on 2006-02-24
The downloaded .debs are stored in apt's cache directory. I guess it could be possible to make a CD, but I'm not sure what all would have to be done to get it to work, if possible. I think a simplier solution might be to take the home box to work and plug into their network if you are allowed.

---

### Post by cotcot on 2006-02-24
Is your home PC comparable to the other one ? If yes you could consider cloning. You can use partimage for that (its an open source app that does what Ghost does). There are some limits you have to check in the docs of partimage.

---

### Post by MarkLori on 2006-02-24
The home machine is a Dell with an Intel processor at about 1.2 Ghz.  The work machine is an HP, also Intel at about 2.4 Ghz.  I imagine that would give me grief, though I'm not sure.

I'm not really worried about the Xubutu part (just want to play with it really) at home, just getting Automatix to look at the deb files.  I could put them on a data cd and pu them in the cache directory at home.   Would that make it see them correctly and work, or should I carry the machine in?  (I'd rather not confuse people at work by bringing in a machine that doesn't belong to the company)

Thanks for the ideas!

Mark

---

