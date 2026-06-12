---
title: "help with partitions ,, and backup?"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by darklaos on 2011-10-11
hey im trying to install ubuntu on my acer d255e, but it has 3 primary partitions with window 7 starter.. i could format it but i dont want to lose the license 

so im wondering if i could backup the recovery partition and why not the other 2 i want to move them on a extended partition.

or theres a way to change them from primary to logical partition?

im a bit confused, since i cant create more than 4 primary partition and i dont wan to install ubuntu on logical partitions  help D:

---

### Post by Quackers on 2011-10-11
Ubuntu will be fine installed into a logical partition. It's Windows that won't (normally) boot from a logical partition.
You need to make sure that you are currently using only 3 primary partitions though. That includes any 200MB boot partition.

You should also make the Windows recovery dvd's to be safe.

---

