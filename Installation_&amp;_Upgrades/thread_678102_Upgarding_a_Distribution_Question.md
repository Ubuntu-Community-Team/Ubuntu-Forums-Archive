---
title: "Upgarding a Distribution Question"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by MianoSM on 2008-01-25
I am currently using 6.06.1 LTS for a server that I'm hosting, and plan on upgrading in April when the new LTS is released.

In doing so I am curious as to whether or not the Kernel will also be upgraded then the distribution is upgraded?

---

### Post by Rocket2DMn on 2008-01-25
Yes, the kernel will be upgraded.  I think it will be using 2.6.24

---

### Post by MianoSM on 2008-01-25
Excellent! To further sate my curiousity then will the kernel be configurable as it is upgraded?

I ask this because I would like to change it from 100hz up to 1000hz. Thanks again! = )

---

### Post by Rocket2DMn on 2008-01-25
I'm not sure on all the details, but any linux kernel can be configured, you would just have to recompile it yourself.
Something like CONFIG_HZ=1000
It appears that the desktop default is 100 and server is 250 (just from a quick google search, don't quote me on that)
You probably know more about it than I do, but that's the gist of it.

---

### Post by rosegarden78 on 2008-01-25
> **MianoSM said:**
> I am currently using 6.06.1 LTS for a server that I'm hosting, and plan on upgrading ... In doing so I am curious as to whether or not the Kernel will also be upgraded ... ?

My kernel was upgraded but so were the features in Ubuntu Gutsy Gibbon 7.10 is the only version I use tried a Hardy Alpha 3 network upgrade to no avail.  I use a setup as described [here]("http://ubuntuforums.org/showthread.php?t=677959") and [here]("http://ubuntuforums.org/showthread.php?t=385981").  If you want to upgrade to GG I highly suggest burning your own 4x CD-R instead of a network upgrade.  Make sure to backup your /home folder before upgrading.

---

