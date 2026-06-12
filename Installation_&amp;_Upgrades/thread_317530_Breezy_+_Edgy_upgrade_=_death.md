---
title: "Breezy + Edgy upgrade = death?"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by spectre_25gt on 2006-12-12
So, I tried to a dist-upgrade yesterday from Breezy to Edgy. Things seemed to be going alright. There were one or two packages that didn't like each other, but I managed to fix the conflicts. Then, once the upgrade finished, I noticed that any command that required  a permissions check was taking a very long time. Against my better judgement, I decided I'd try to reboot the server. Unfortunately, that totally did me in. The next time it came up (and I use the term loosely) it showed about 50 segfaults while loading the kernel and mentioned something about not being able to mount $BUNCH_OF_GARBAGE. 

So... I'm pretty certain the server is hosed at this point and I've burned an install CD for Edgy. What I'd really like to know is what went wrong. Did I do something incredibly stupid or did something happen that shouldn't have?

Any insight would be greatly appreciated. Thanks.

---

### Post by wpshooter on 2006-12-12
IMO, it is always better to do a completely new install from scratch as opposed to undating from one O/S to another version of that O/S.  It generally did not work very well with M/S windows and I don't think it works very well with Ubuntu/Linux.

---

### Post by spectre_25gt on 2006-12-12
Even on a windows machine doing an upgrade should never do something like this. Something must have really gone wrong here.

---

### Post by spectre_25gt on 2006-12-13
Ok, it looks as though there might be a hardware issue with the computer. I tried to boot to a new install CD last night and I kept getting "hda: lost interrupt". I've read that this can be incompatibility with hardware, which would make sense since it's a new CD and a new upgrade that I'm having trouble with. I'm thinking  about just building a new server. I've decided on a case, but I still need to find a mobo, processor and raid controller. I'll probably also end up getting some larger hard drives.

---

