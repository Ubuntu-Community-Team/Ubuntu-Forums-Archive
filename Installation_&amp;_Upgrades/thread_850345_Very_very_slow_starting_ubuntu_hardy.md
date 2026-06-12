---
title: "Very very slow starting ubuntu hardy"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-07-05
I have reinstalled ubuntu hardy, all went very well, it used to start fast, but lately the passed 2 days ubuntu hardy has been very very slow to start, I mean when I start the computer the screen that show Ubuntu, the first screen, is very very slow to passed.

 ,

---

### Post by Sam Lars on 2008-07-05
Is it slow the whole way through or does it seem to get stuck on one specific spot?
In the Grub menu on boot, look at the list of kernels.  You should see something like 2.6.24-19.  If there are other entries with a different number, like 2.6.24-18 or -17, try booting those and see if they are any faster.

---

### Post by SkonesMickLoud on 2008-07-05
You could also try Readahead:

[http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

---

