---
title: "Low disk space after upgrade to 6.06"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by markiss on 2006-07-02
Before I upgraded I had about 2 gigs left on my 6 gig drive. Now I'm at 95% full. When I boot using the grub boot loader (I dual boot with XP on another drive)I notice there are several earlier versions of ubuntu listed. Can these be deleted? And what other things can I do to reclaim disk space?

---

### Post by reacocard on 2006-07-02
open synaptic. to remove the earlier kernels, search for "linux image". once you've done that, go to Settings -> Preferences -> Files  and click "Delete Cached Package Files"

---

### Post by FredB on 2006-07-03
or in the terminal : sudo apt-get clean.

---

### Post by markiss on 2006-07-03
thanks, I have 1.5 gigs of space now :D

---

