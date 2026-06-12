---
title: "[SOLVED] Yet another Triple Boot Question"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by robertj20112 on 2008-07-30
I've read a lot of threads about triple booting, but they all seem to be slightly different and, frankly, me head is spinning!  I do hope someone takes pity on this poor noob and offers some good advice!  Thanks in advance.

My computer is Intel quad-core, hd0 is 500GB with 5 partitions, hd1 is 320GB with two partitions.  XP was installed first on hd0, partition 1.  Vista installed second on hd1, partition 2.  Want to install Hardy on hd0, partition 5, in a triple boot configuration.  My questions are:

1.  Can this be accomplished by installing within Windows by picking the correct version (XP or Vista) from which to install it, or should it be installed from Hardy CD directly into the chosen partition?

2.  If the answer to #1 is yes (i.e., can be done within Windows), should it be done within Vista or within XP?  (Vista is aware of XP but not vice-versa, but XP is on hd0!)

In other words, I'm stumped!  I've installed Hardy on another computer with XP, and that was a piece of cake!  That was done from within XP.  Now I'm hooked on Hardy and want it on my main computer!  Any help will be welcome.  Thanks.

---

### Post by robertj20112 on 2008-08-01
After several false starts, I was able to successfully install Ubuntu in a triple-boot configuration following the steps given in here:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

There is still some confusion on my part about why the author chose the exact wording of Step 6 in the above link.  After starting out the step referring to sda, he seems to base his selection on an sdb entry, which in my case was the wrong disk drive!  Anyway, I made the correct choice, rebooted, went into Vista and added Ubuntu to the boot choices using EasyBCD as described in the above link, and everything works!

Hope this resolution might help someone else.  The prize (Ubuntu) is worth the effort!

Cheers!

---

