---
title: "Fresh install clarification(s)"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by The Glidd on 2010-01-13
I was a Jaunty user and then updated to Karmic.  Wireless went from being sporadic in Karmic to non-existent after I tried the wrong fixes.  I've changed so many settings and tried so many fixes that I don't know which way is up with the wireless.  

I'd like to start from scratch.  If I install from CD, will it just write over my current ubuntu partition?  Will the contents of home stay intact or will everything disappear?  Do I have to create a new partition?  

Thanks!

---

### Post by darkod on 2010-01-13
Unless you have /home as separate partition, it will get wiped by the new install. If your ubuntu is still working even without wireless, copy everything you need to external hdd or similar.
Then in the next install you might consider creating manually /, /home and swap partitions and that way in future clean installs you keep your /home.

If you already have separate /home, you will only format / and that will wipe this messed up install but it will keep your /home intact. But you have to use manual partitioning and tell it to use existing /, /home and swap partitions with the difference that you FORMAT / and DO NOT FORMAT /home.

---

### Post by The Glidd on 2010-01-13
Ok, sounds like I need to back-up /home.  

When I do the fresh install, what am I electing to do to so I write over the currently used partition.  Will this be obvious enough?

---

