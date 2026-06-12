---
title: "Recommended Partition Sizes/schemes"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by esmurdo on 2008-11-16
So after finally getting 8.10 to work with my Atheros card, I'm ready to wipe the entire drive and start fresh with 8.10 as my only OS. My question is: What is the best and most useful/efficient partition setup? I've had conflicting reports on the SWAP size and whether or not to setup a standalone partition for /TMP and /VAR. Here is what I'm thinking of doing so far:

HP Pavilion dv9910us
Intended use: Music, movies, some simple games, web surfing, image editing and office work.
HDD Size: 250GB
RAM Size: 3GB (expandable to 4GB later)

UBUNTU 8.10 x64 Desktop

SWAP  - 4GB
/     - 15GB
/BOOT - 200MB
/TMP  - ?
/VAR  - ?
/MNT  - 10MB
/HOME - Remainder

Any help would be appreciated!

---

### Post by Pumalite on 2008-11-16
I'd go with '/' and 1 GB of /swap; unless it's a laptop: then /swap=1,3 of RAM if you want to hibernate

---

