---
title: "/home Partition"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by TunaCanTommy on 2012-09-22
Can I use the same /home partition (same UUID) for two different Ubuntu installations; i.e. 12.04 and 12.10?

---

### Post by jrog on 2012-09-22
> **TunaCanTommy said:**
> Can I use the same /home partition (same UUID) for two different Ubuntu installations; i.e. 12.04 and 12.10?
Yes, but you should probably use two different users between installations, because otherwise they will share the same directory (thus the same configuration files), and things may not work out nicely. Two different users with their own home directories on a shared /home partition works great.

---

### Post by The Cog on 2012-09-22
Sort of. Two different versions of the same software may occasionally use different configuration settings, and on rare occasions this can cause problems. Particularly if you are regularly switching back and forth between versions. You may get away with it, or you may be better off using different users as jrog suggests. For one-off upgrades, it is worth keeping the same folder and be aware that you just might have to delete the settings folder for one or two applications.

Gnome was always my biggest problem - upgrading often caused niggles, and gnome tends to scatter its config across multiple folders, making it  hard to find and remove all the old entries.

---

### Post by jrog on 2012-09-22
> **The Cog said:**
> Sort of. Two different versions of the same software may occasionally use different configuration settings, and on rare occasions this can cause problems. Particularly if you are regularly switching back and forth between versions. You may get away with it, or you may be better off using different users as jrog suggests. For one-off upgrades, it is worth keeping the same folder and be aware that you just might have to delete the settings folder for one or two applications.

Gnome was always my biggest problem - upgrading often caused niggles, and gnome tends to scatter its config across multiple folders, making it  hard to find and remove all the old entries.
Yes, sorry, I was assuming that the OP wanted to keep both installations and regularly switch between the two. If this is just a question about upgrading from 12.04 to 12.10 and keeping the same user and same home directory, then yes, it is quite possible (recommended, I'd say) to keep the same home directory and user between upgrades.

---

### Post by TunaCanTommy on 2012-09-22
Thanks gentlemen, I'll mark this thread solved.

---

