---
title: "Fresh Install Partition Advice"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by whitetimer on 2010-01-11
Hi All

Ok i am going to do a clean cli customised installation of karmic on a 250gb HDD and i would like so advice as to partitioning

I was thinking something like this

/           (system files) - 20GB
/boot       (Boot Up Files) - 5GB
/swap       (Swap Index) - 8GB
/home       (home files) - 217GB

What are peoples thoughts - I am just one week into Linux/Ubuntu, so be gentle ... :D

Many Thanks

---

### Post by tachuela on 2010-01-11
You don't need the /boot partition

---

### Post by SecretCode on 2010-01-11
There only special circumstances where you would need a separate /boot.

How much RAM do you have? You need at least as much swap as RAM if you want to hibernate, but if you have 4GB or less of RAM, 8GB swap is more than you'll ever need.

---

### Post by darkod on 2010-01-11
> **tachuela said:**
> You don't need the /boot partition

+1

You don't need it. And if you still decide to have one, 5GB is way too much space. 100MB or 200MB is more than enough.
The rest is looking good.

---

### Post by whitetimer on 2010-01-11
Excellent, many thanks will discard the boot partition :D

---

### Post by J V on 2010-01-11
and stick the lot in an external, you never know when some free primaries will come in handy...

---

