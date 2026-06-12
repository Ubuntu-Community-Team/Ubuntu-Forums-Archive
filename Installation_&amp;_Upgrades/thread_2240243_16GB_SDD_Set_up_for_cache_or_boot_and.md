---
title: "16GB SDD: Set up for cache or /boot and / ?"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by mike-g2 on 2014-08-18
I've got a Thinkpad Yoga with a 16GB SSD and a 500GB HDD and am trying to decide whether to install the OS on the SSD or use it with bcache (or dm-cache?) as a cache SSD.  

My concern with the first set up is that my linux installs seem to bloat after a few years.  For example, on my current laptop, my root (/) partition with the OS (i.e. not including /home which is on a separate partition) uses 20GB.

Any thoughts or experiences folks have had with either set up will be appreciated.

Thanks,

Mike

---

### Post by ibjsb4 on 2014-08-19
Any files that do not need to be saved to hdd can be stored in tmpfs (provided you have enough ram).

A root system of that size is hard for me to image.  Do you clean from time to time?  I find that BleachBit works well for this, just have a care when using it.

If I had a SSD I would want my OS on it, maybe one day :)

---

### Post by mike-g2 on 2014-08-20
I did a little poking around and discovered that there were some very large and unnecessary -dbg  and LaTeX support packages installed, old config files, and that Mathematica 9 takes up almost 6GB!   Cleaning this up got me down to ~10GB so I decided to use the SSD for / and /boot.  The machine boots in <10 seconds, which I'm very happy with.

---

### Post by ibjsb4 on 2014-08-20
10 seconds .. wow ..

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

