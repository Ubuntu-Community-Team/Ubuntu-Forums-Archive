---
title: "Swap - Primary or Extended"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by BrokeBody on 2007-04-22
Is your swap partition primary or extended. How should it be?

I always set up my swap and my root partition as primary, but I was wondering, should I set up swap as extended from my primary root partition, or it doesn't matter whether it's going to be primary or extended?

---

### Post by heimo on 2007-04-22
Doesn't matter. I happen to have it on extended / logical partition. Formerly, I used to keep it close to beginning of the disk because that's a bit faster, but ... when your system starts to swap extensively,  it really doesn't matter. It's slow anyway. But if you happen to have multiple disks, you can create several swaps (one on each disk), and your system will use the one that's least busy.

---

### Post by GeDaMo on 2007-04-22
I use a swap file rather than a partition.

---

### Post by heimo on 2007-04-22
> **GeDaMo said:**
> I use a swap file rather than a partition.

That should work fine too. If anyone is interested, here's how to do it:
[http://ubuntuforums.org/showpost.php?p=287528&postcount=6](http://ubuntuforums.org/showpost.php?p=287528&postcount=6)

---

