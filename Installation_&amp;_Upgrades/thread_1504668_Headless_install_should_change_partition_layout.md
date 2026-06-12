---
title: "Headless install should change partition layout"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by TheTank on 2010-06-08
Hello everyone,

I have a problem with a version of Debian/Ubuntu I supply.
It is an ISO that customers can install headless.
In the last version we had a simple 2 partition layout (root and /home).
In the next version we will also be needing a partition for DRBD.

From my limited knowledge, when I change the preseed settings for the partitioning, it will wipe the existing data.
This is not good.

Now I know that the Ubuntu installer, when it detects an existing installation, will prompt you and allow you to keep the partition next to the standard installation.

What I would like is to have it both ways:
1) no existing partition scheme found -> slap on the preconfigured partition
2) existing partition found? -> modify it to match the preconfigured partition (setting up logic via script is fine)

can this be done?

thanks!

---

### Post by TheTank on 2010-06-09
btw, is this the right sub-forum or should I aks to have it moved elsewhere?

---

### Post by TheTank on 2010-06-09
Update:
found this [link]("http://www.enricozini.org/2008/tips/d-i-conditional-partitioning/"), though it does not really clear up my questions.

---

### Post by TheTank on 2010-06-10
I'm gonna keep posting my ideas and findings in here, just in case someone is interrested.

Another idea would be to not handle partitioning beyond swap and root, but provide a package that will do the partitioning on use-case basis.
Then we could provide different packages (with different versions) that handles partitionings.

---

### Post by TheTank on 2010-09-21
Me again. I may now continue on this task though I would check out the lucid iso and see if there is anything I could find.
Sadly I was pretty lost.

Seeing as the installer basically does exactly what I need, I though I'd 'inspire' myself from it. Yeah, ok, FINE! I'd blatantly  copy it. ;)

Greps for 'partman', 'd-i' or 'bootable' did not really get me far.
The preseeds give me nothing I could call usable.

Can anyone point me out what I should be looking for?

---

