---
title: "20GB partition Scheme recommendations ?"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by 5-HT on 2005-08-16
Hi, I'm new to the Linux world and have tried out some live cd's from various distros and find Ubuntu simply amazing (not to mention the forum...everyone's great, and I've learned so much from simply browsing around). 

I'd like to install Ubuntu on a single boot system consisting of a 20GB hard drive with 256MB ram (rather antiquated, but my only system), utilizing the common three partitions consisting of /, /home and swap. 

After searching around the forum I've seen rather conflicting results on what would be an adequate space for a root partition...varying from 2.5 GB through 10GB with the norm around 5GB.

I'm just wondering if anyone can help out informing me around how much space Ubuntu takes up under a normal installation ?

I'm not looking to install every package under the sun...just the default with possibly some extra multimedia and office programs mostly.

From what I've read if seems like setting up 512MB swap, 9.75GB /, and 10GB /home partitions may be the best way to go, but was just wondering if anyone has any recommendations?

Thanks for any feedback.

---

### Post by jasmuz on 2005-08-16
Under a normal install from disk it takes from 1.3 to 1.6 Gb, you should have at least from 7 to 9 gb for /, 2x your ram for swap = 512 megs, and the rest for your /home folder.

---

### Post by heimo on 2005-08-16
I have quite default Breezy install with same partitioning scheme (except my /home is on it's own disk). My root partition takes approx. 2GB at this moment, but it includes /var (which has .deb packages on it), /tmp and other variable factors.

I would probably divide that disk into 768MB swap, 5GB / and rest for home. Your 10GB/10GB plan will work too. If you're uncertain, you could just make one big / with home, but it's of course easier to reinstall if you have /home on its own partition.

Someone will probably suggest LVM (logical volume management), with LVM you can make dynamic allocations - it separates partitions from physical volumes and makes possible to grow partitions from a pool of free space. That's very handy, but a bit complex for a simple desktop system.

---

### Post by 5-HT on 2005-08-16
Thanks for the input jasmuz and heimo !

Yeah, it seems approx 9 GB would be good for /.
 Didn't want to sell myself short for space...but then wanted to make sure there'd be enough for /home, oh well there's a tradeoff in everything I guess.

In terms of swap, I always though roughly 2X ram is a good ballpark, though after reading some posts it seems like either 1) the swap isn't even being utilized for some people, or 2) it's being used to the max, with a very slow experience. 

Also, the LVM is a great suggestion. I came across it in another post and looked into it. Beautiful concept, but seems a tad difficult to administer....well I've got some research cut out for me.

Thanks again.

---

