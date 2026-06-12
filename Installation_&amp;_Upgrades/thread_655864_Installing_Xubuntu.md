---
title: "Installing Xubuntu"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by lin2k4 on 2008-01-01
Hi, I booted up Xubuntu from the cd and ran install. I don't know how I should partition the hard drive. I have a 120 GB hard drive with Windows XP installed on a 90 GB partition. The rest is unallocated. The prepare partitions screen shows devices /dev/sda1 and free space.
Also, is there an IRC channel for ubuntu?

---

### Post by mdpalow on 2008-01-01
I loaded Xubuntu for a very short while to check it out, but didn't like it very much. I can't even remember how I allocated space for it, but I can give you some input based on how to install Ubuntu and maybe you can use the same formula.

You have 30 gigs left:

10 gigs for /
18 gigs for /home
2 gigs for a swap drive

First two are formatted EXT3 and the swap you don't have to put in anything.

Hope it helps a little...

---

### Post by lin2k4 on 2008-01-01
What should partition type, location, and mount point be?

---

### Post by jken146 on 2008-01-01
10G mount point: /     filesystem type: ext3

about 1G  swap     type: swap    no mount point
(more than a gig of swap is a waste of space really.)

the rest:    mount on /home   ext3



By the way, I think Xubuntu is great.  So much smoother than Gnomebuntu, runs a lot faster.

---

