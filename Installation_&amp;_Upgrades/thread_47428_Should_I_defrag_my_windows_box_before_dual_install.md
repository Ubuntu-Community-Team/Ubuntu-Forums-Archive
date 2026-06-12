---
title: "Should I defrag my windows box before dual install?"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by fizgig on 2005-07-08
Subjet pretty much sums it up.  I defragged my laptop's 60gig hard drive before using the partition editor that comes with mepis to carve off a 20gig chunk.  I later installed Ubuntu over that chunk.  As such, I don't have much experience with Ubuntu's partition process.

So, if someone who has xp on his laptop already and he wants me to install ubuntu on it, is there a best practice to follow to make sure the windows data doesn't get hurt?

---

### Post by sigma2805 on 2005-07-08
defrag then run scandisk if you can. I also had to turn off the windows swap for the installation but you might be able to install it without that step.

---

### Post by mingus on 2005-07-08
The Ubuntu partitioner is similar to what you used with Mepis, the main diff is the interface.  Ubuntu's is graphical-text (vs a gui) and certainly not as intuitive.

While many advise simply letting the Ubuntu partitioner downsize an existing W$ partition, and this does work most of the time, it can also cause a problem.  You were right to defrag in advance.  IMO, chkdsk /r should be run before the defrag.  The Ubuntu partitioner won't have a problem moving the data, but if a broken filesystem pointer or a bad disk sector is encountered, it may fail.

Hope that helps.

---

