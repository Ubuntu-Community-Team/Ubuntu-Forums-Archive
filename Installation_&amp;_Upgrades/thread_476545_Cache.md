---
title: "Cache"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2007-06-17
Downloaded 61 updates last night.

Where do the files get cached?

I'd like to verify that all were deleted.
Especially as there was a lost phone connecton, and then a power outage a few hours later.

---

### Post by ubuntuguru on 2007-06-18
check /var/cache/apt/archives they should all be in there

---

### Post by Howard Kaikow on 2007-06-19
> **ubuntuguru said:**
> check /var/cache/apt/archives they should all be in there

THanx.

I learned last night that apt-get clean is supposed to clean out the critters.

---

### Post by Howard Kaikow on 2007-06-19
What happens when tere are future updates?
Are the old files in the cache deleted?
Or is everything retained?

---

