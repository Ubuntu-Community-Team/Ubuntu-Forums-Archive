---
title: "Debootstrap reports corrupt files during installation"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by shimmip on 2010-06-27
I realise it might be a bit wierd to post when I already know the answer, but I looked on the forums for an answer to this and nothng worked. When I worked out what I had actually done wrong, I suspect other people who have encountered this issue may be afraid to admit to it! Most responses seemed to be along the lines of reburning CDs or installing from USB. This was nothing to do with the cause of my error.

Basically what had happened was that when I partitioned the hard drive, I set up a partition of 20 MB instead of 20 GB to install the system and a swap partition of just 12 MB instead of 12 GB. The alternate installer doesn't flag this as an issue and starts the installation, but almost immediately runs out of space and falls over with the debootstrap corrupt file messages. I can see why these messages would lead people to believe the CD was corrupt, but I got the same with additional downloads, with newly burned CDs and attempting to install from USB. I later confirmed that all of these worked fine once I had sorted out my partitions.

When I was using the manual partitioner, the default space for the partition showed up as the full size of the drive in GB - 120.0 GB in my case. I deleted this and keyed in the size of partition I wanted, and because the previous figure had been in GB, I assumed that to get a 20 GB partition I would have to key in 20. I didn't read the text carefully basically, and this gave me 20 MB. You can key the figure in GB, but you have to include the letters GB afterwards as in the default figure, so by keying 20.0 GB you actually get 20.0 GB.

The upshot is, if you get this error during installation, check the size of your partitions before burning a dozen different CDs.

Hope this helps someone now that I've revealed myself as a muppet! ):P

Phil

---

### Post by Tristan Schmelcher on 2012-12-18
2+ years later, I hit this same unhelpful error message, and for the same reason! Typed 20 MB when I meant to do 20 GB.

Thanks for sharing your wisdom.

---

### Post by oldos2er on 2012-12-18
Old thread closed.

---

