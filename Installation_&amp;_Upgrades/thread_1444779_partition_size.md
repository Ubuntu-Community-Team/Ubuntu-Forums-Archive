---
title: "partition size"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by Jpenguin on 2010-04-01
I'm doing a fresh install [again] and this time I want to create separate partions for- /home, /usr, & root.   I'm using the alternate install CD, could some1 gime me instructionss and size recomendations.  I will not be using EXT4, my HD is 600GB, I will have win7 in vmWare.  I am a gamer and a programer (java, c++, Obj-c,FreePascal...)

EDIT:

/boot
swap
root
/home

---

### Post by Jpenguin on 2010-04-01
I tried-

/boot- EXT3- 250 MB
/home- EXT3- 250 MB
/root - EXT3- 375 GB
swap- 12 GB

Hope it works!

---

### Post by oldfred on 2010-04-01
I think your root is too large and /home way too small. You do not need that much swap unless that is your RAM and you hibernate.

My system has all data in data partitions and I have used 5GB for root, 1GB for home and 3GB for swap. If all your data goes into /home it could be many GB depending on what you save. I recommend 10-20GB for root if home or data are not in root.

---

### Post by Slim Odds on 2010-04-01
> **oldfred said:**
> I think your root is too large and /home way too small. You do not need that much swap unless that is your RAM and you hibernate.
....

Agreed.

Also, the OP is confused about /root. You don't want /root, you want /

You only need about 10-15 GB for /

I have a 22 GB / and a tons of stuff installed; it's still only about half full.

---

### Post by srs5694 on 2010-04-01
The original post mentioned a separate /usr partition. If that's used, then most desktop installations can use a / (root) partition of about 1-5GB, with a /usr partition of 5-20GB, depending on how much is installed. If /usr isn't split off, then those values should be combined for the / (root) partition (6-25GB).

---

