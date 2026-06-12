---
title: "Swap partition size?"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2010-05-10
I pulled an old drive, which I just remembered had my swap partition (oops).

So how big does the new swap partition need to be? I guess it can be created only from Live boot? Or can I do it with Ubuntu booted?

---

### Post by bananas4370 on 2010-05-10
You don't have to have a partition for swap. You can always use a swap file. Go [here]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/") for more information.

---

### Post by darkod on 2010-05-10
> **Moozillaaa said:**
> I pulled an old drive, which I just remembered had my swap partition (oops).

So how big does the new swap partition need to be? I guess it can be created only from Live boot? Or can I do it with Ubuntu booted?

Earlier it was about twice the size of RAM but with computers these days having loads of RAM that's wasting space for swap partition of that size. Plus the more RAM you have, less probability of swap even getting used.

However, it seems if you want to hibernate your computer regularly, make swap at least 1.5 x RAM, so it can hibernate. I don't use hibernate, so I can't say more.

Otherwise, about 2GB swap is more than plenty, doesn't need to be twice the size of RAM any more.

For example I have 6GB RAM and 2GB swap, and when ever I checked swap use was on 0%.

---

