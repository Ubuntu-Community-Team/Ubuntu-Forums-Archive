---
title: "Upgrade to 8.04.1 hangs"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by Grapple on 2008-08-14
Was upgrading to 8.04.1 using the alternate CD, and it got some way in then just hanged, so now I'm neither one thing or the other with no PC.

A quick trawl seems to indicate that my only option is to do a full install, however the install process seems to require the hard drive to be re-partioned. I really dont want to do this, I have the drive nicely partioned, all I want to do is to install hardy heron where before I had gutsy gibbon. Is there a way to do this...?

I have a live CD and it does boot from this ok, I also have the alternate CD, but thats no use, nor is the minimal CD iso I've downloaded.

So the basic question is, can I use the live CD to install 8.04 into the original partition, ie continue the upgrade not do an install...?

Tim

---

### Post by Pumalite on 2008-08-14
You can install on top. Go 'Manual' and use the old partitions. You can ignore /swap
Save your data first.

---

### Post by Grapple on 2008-08-14
You mean from the Live CD do a "manual" install...?

I can see the original 7.10 partition from the Live CD, and I've started the package manger, but there doesnt seem an obvious way to steer the package manager to installing into this partition...

Also, which of the huge number of packages that are buried on the CD are the ones I need to install...? As opposed to the ones I might want to install...

Tim

---

### Post by Pumalite on 2008-08-14
In the Live CD; when you come to the partitioner, go 'Manual'

---

### Post by Grapple on 2008-08-15
OK, that worked, thanks...

Although there were a few choices to be made that would look scary to the completely uninitiated.

However I still lost various installed applications, eg Anjuta.

Is this because of doing the manual install, or would it have happened anyway?

Tim

---

### Post by Pumalite on 2008-08-15
All your programs are new now. If you followed my instructions; this is a clean install.

---

