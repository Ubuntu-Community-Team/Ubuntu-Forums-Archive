---
title: "Any way to permanently deselect particular update?"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by Nordvind on 2011-11-29
Is there any way to **permanently** deselect particular update? I don't need much of the stuff, like translation updates to 30 languages and so on. 
When I deselect a package, it still stays in update manager, and clutters the view, and what is worse, is selected by default.

P.S. I believe, it has something to do with [this bug]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/90105").

---

### Post by zvacet on 2011-11-29
You can go to the synaptic and find languages you don´t need and remove them.You can not get updats for something that doesn´t exist on your system.

---

### Post by Nordvind on 2011-12-01
Nice advice, for some reason I just didn't think of it :)

But the functionality lack, what the linked bug is about, still persists. It isn't connected to the topic, actually, I just noticed it, while trying to get rid of unnecessary updates. Guess I'll have to get my hands dirty, and try to fix it.

---

### Post by zvacet on 2011-12-02
In synaptic find languages you don´t want to update > mark them > I think it is package tab ( but you will find ) l**ock version**.

---

### Post by OrangeCrate on 2011-12-02
> **Nordvind said:**
> Is there any way to **permanently** deselect particular update? I don't need much of the stuff, like translation updates to 30 languages and so on. 
When I deselect a package, it still stays in update manager, and clutters the view, and what is worse, is selected by default.

P.S. I believe, it has something to do with [this bug]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/90105").

Adding...

When you don't know which package exactly you want to uninstall, in synaptic, go File > History, and browse for the update. Then cut and paste (or whatever) to the search box and find it, and uninstall it, as already suggested.

For language clutter specifically, install the localepurge package to keep things tidy.
Follow the guidelines in this tutorial:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

(Don't let the date of the thread fool you - it's as valid today, as the day it was written.)

---

