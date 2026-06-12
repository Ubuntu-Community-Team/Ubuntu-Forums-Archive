---
title: "Updating form 10.04 to 10.10"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by Refreshe on 2011-01-07
When I try to update I get [THIS]("http://www.mediafire.com/i/?46s2d98avjyj84f") at about half way. I have no clue what the problem is.

---

### Post by Idefix82 on 2011-01-07
Do you have /home on a separate partition? If you do, then it might be easier and safer to do a fresh install instead of an upgrade. You will be able to keep all your personal files by using the current /home partition in the new installation.

---

### Post by Refreshe on 2011-01-07
Sadly no. This is just my programming laptop with a small HD. I dont need 10.10 but I would like to have it.

---

### Post by efflandt on 2011-01-08
Have you added any ppa repositories for video or audio drivers (like for newer video drivers or HDMI audio, etc).  If so, you need to purge those first.  I am no expert on that, but I would think you need to at least uninstall such packages and uncheck those repositories in Synaptic, then hit the reload icon and close Synaptic before trying the upgrade again.

---

