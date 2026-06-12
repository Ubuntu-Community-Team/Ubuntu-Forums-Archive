---
title: "How do I load RAID drivers during installation?"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by N1ghtF4lcon on 2006-06-18
Hi everyone,

I'm trying to install Ubuntu Server 6.06 on my home box and I need a bit of help. How do I go about loading drivers for my RAID controller (Broadcom RAIDCore BC4852) during the installation?

Broadcom provides a driver SDK using which I can build the drivers from source. I've done that already on a different Ubuntu 6.06 install. Now I have two files - bcraid.ko and bccfg.ko, and my guess would be that I need to load these two for the installation to be able to work with my RAID controller.

Is there an easy way of doing this? As an alternative, would it be possible to install Ubuntu from another existing installation? For example, I can hook up a regular IDE drive to that box, install Ubuntu on that, boot it up, load the RAID drivers, mount my RAID5 array and then run another install onto the array. Not sure how to do that either, but if it's possible, I can certainly give it a try.

Would appreciate any help on this. Thanks!

---

### Post by N1ghtF4lcon on 2006-06-19
Am I really the only one who has ever needed to load 3rd-party drivers? I've searched everything I could think of for an answer, so far nothing. Please help...

---

