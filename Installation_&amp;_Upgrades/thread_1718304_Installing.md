---
title: "Installing"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by Colo2 on 2011-03-31
Hello

Is there a way to install ubuntu keeping my current home folder intact, and not overwriting it? 

My home folder isn't on a separate partition.

---

### Post by Sean Moran on 2011-03-31
> **Colo2 said:**
> Hello

Is there a way to install ubuntu keeping my current home folder intact, and not overwriting it? 

My home folder isn't on a separate partition.
Quite a few different ways.  Simplest way is to reduce-move your partition down by 8GB or so and create a new partition in the vacant space.

More complex would be to copy your home directory (just the past for your user, eg. home/colo and no neded to copy the entire /home directory.) to another partiiton and then put it back when the next distro is installed.

To keep things intact, move your home directory to a new partittion, and then during the install, select that partitiion as /home and use the same username etc. so that the new installation (hopefully) uses that same intact data on the new partition for your new user.

---

