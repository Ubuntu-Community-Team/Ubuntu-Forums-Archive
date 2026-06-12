---
title: "10x 64Bit Server - Can't authenticate to do upgrade."
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by nakedgoat on 2011-12-21
started off with not being able to install a program via apt today; 
so I logged in via NX graphically to look around, (the problems was sayign most of my repos were no good)  when I got to the GUI it's saying that my current version is no longer supported and to upgrade to 10.04.3 LTS

So I am trying to use the upgrade option it downloads two files then fails with "Authentication fail authenticating the upgrade failed. There maybe a problem with the network or server."

There's not and I'm not able to run sudo apt-get update && sudo apt-get upgrade, but I was able to update the software I needed to via the GUi installer, but then it gave me that message again about old software not supported and advised me to upgrade, however I can't update/upgrade if I can't auth to do so...

Sorry if this is a "repost" I spend a bunch of time looking around for a SOLVED answer, there has to be something besides building a USB key to upgrade from??

EDIT: Oh here's what it says when I try to check for software updates via GUI:

**"Your Ubuntu release is not supported anymore you will not get any further security fixes or critical updates. Please upgrade to a later version of Ubuntu Linux."**

Any help would be great! thanks in advance! :)

---

### Post by zvacet on 2011-12-21
Witch version do you run 

```
lsb_release -a
```

to find out.

---

### Post by nakedgoat on 2011-12-28
> **zvacet said:**
> witch version do you run 

```
lsb_release -a
```to find out.


9.10

---

### Post by nakedgoat on 2011-12-28
> **nakedgoat said:**
> 9.10


Trying to force an update... so far only one warning

WARNING: Failed to read mirror file

---

### Post by nakedgoat on 2011-12-28
> **nakedgoat said:**
> Trying to force an update... so far only one warning

WARNING: Failed to read mirror file


Got the same error again, wonder if I should stop of the update, and do a partial, then try a full.. right now its trying to do the full update anyway... I don't want to end up with a non-functional server!

---

