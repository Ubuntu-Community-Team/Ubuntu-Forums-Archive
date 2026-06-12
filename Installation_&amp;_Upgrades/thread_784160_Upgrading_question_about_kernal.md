---
title: "Upgrading question about kernal"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by TuckLive on 2008-05-06
Two quick questions

If I upgrade from 7.10 to 8.04 will the kernal update completely or will I have 2 kernals?  I've heard of people with other distros having remenants of the old kernal after an upgrade.

Also if I remove the Windows partition can I set my current Linux partition to "take over" the unused space without having to reinstall?

---

### Post by solitaire on 2008-05-06
I'm not 100% sure 

But if the upgrade works you should only have 1 Kernal listed. There is usualy only 2 listed when the update is running to let you boot in to a known working Kernal if the upgrade fails.

saying that I upgraded the kernal from:

Ubuntu 8.04, kernel 2.6.24-16-generic
to
Ubuntu 8.04, kernel 2.6.24-17-generic

A few days ago and I still have both listed in the Boot menu. I seee no real harm in having both.


As for taking over the hard drive.

Best bet is top use a live CD to remove the windows partition and use 'Parted' to expand the linux partition (or create a separate '/Home' partition so you don't loose everything if your install goes belly up) :)

There are a few posts in the Forum on how to move your '/Home' folder to a separate partition.

---

