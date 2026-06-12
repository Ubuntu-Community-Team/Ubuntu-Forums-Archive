---
title: "Ubuntu -&gt; Windows dual boot"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by pepsifx357 on 2008-06-24
I have Hardy Heron installed on my 80gig hard drive and I want to partition that 80gig to two 40 gigs and put windows on the other partition.  How could I do that and have the ability to dual boot.  I tried this one time and the grub boot loader didn't load and I lost the ability to get back to ubuntu.

Thanks,
Ben

---

### Post by geezerone on 2008-06-24
You would probably be best using Gparted Cd to shrink the partition disk size which has a nice gui.

The supergrub disk is a useful addition to any CD collection and will allow you to boot into Ubuntu if grub isn't working too.

Also, take a look at** [this]("http://users.bigpond.net.au/hermanzone/") **good site regarding grub

---

### Post by thschiavo on 2008-06-24
The first time I tried it, I did something wrong: the mount point :confused:. After that, I observed that some friends did the same. Is this the problem? When I use as mount point "/", everything just works fine:popcorn:.
Usually the installation of Ubuntu sets the mount point as "/media/sdan" (n integer). Could this be the real mistake in an Ubuntu Installation?

---

### Post by pepsifx357 on 2008-06-25
I'll try that thanks

---

