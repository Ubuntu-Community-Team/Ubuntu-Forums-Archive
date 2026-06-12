---
title: "Now that Hoary is final - what about backports?"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by Psquared on 2005-04-08
To do an update from Warty to Hoary Final do I still have to get rid of all the backport stuff I installed and then do the update? For example, I've got Firefox 1.0.2 already - plus other stuff. I also have multiverse and universe enabled. I read on another thread I need to rem that out in my sources.list.

Thanks in advance.

---

### Post by bored2k on 2005-04-08
Erase your warty backports repositories and put this ones:
> deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

Then apt-get update/upgrade.

---

### Post by jdong on 2005-04-08
We discussed this quite a bit in the Backports forum. In short, everything should upgrade normally, except for Synaptic, which requires an "apt-get install synaptic/hoary" after you finish the upgrade.

Simply follow the general directions to change all instances of Warty to Hoary.

---

### Post by bored2k on 2005-04-08
For any information, visit
[http://ubuntuforums.org/showthread.php?t=12174](http://ubuntuforums.org/showthread.php?t=12174) .

---

