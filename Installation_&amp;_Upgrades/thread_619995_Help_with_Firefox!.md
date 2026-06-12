---
title: "Help with Firefox!"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by DavGerm4 on 2007-11-22
I don't know if this is in the right section, but when I was going to listen to music on a myspace page, I had to install the missing plugins!  So I looked to see what to install, and the first one was Adobe Flash, and the other one I can't even remember!  Anyways, I installed the one I can't even remember the name first, and when I reloaded the myspace page, the music bar is all glitchy and won't play or anything.  I thought it was just because I didn't install Flash, so I went ahead and did that!  It is still doing that weird Glitchy thing on the Computer!  Does anyone know why this is happening!?  Does anyone know if there is a way to remove updates from Firefox?!  Thanks, I'm kind of new at all of this!

---

### Post by aysiu on 2007-11-22
It's possible you might have installed Gnash instead of Flash?

Go to System > Administration > Software Sources, and make sure all the sources (except CD-ROM) are checked. When asked to reload, reload.

Then go to System > Administration > Synaptic Package Manager, search for *gnash*, mark it for removal. Search for *flashplugin-nonfree* and mark it for installation. Click Apply.

Then close Firefox and restart it.

---

