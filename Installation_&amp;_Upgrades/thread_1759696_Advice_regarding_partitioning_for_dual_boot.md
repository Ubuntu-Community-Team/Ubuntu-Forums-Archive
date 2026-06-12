---
title: "Advice regarding partitioning for dual boot"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by jorritTyb on 2011-05-16
Hi all,

At the end of this week I'm going to get a new PC. It will have a 80GB SSD ( 2.5" SSD INTEL X25-M 80GB) and a 1TB HD. I want to dual boot Windows 7 and Ubuntu on it.

The SSD will be for fast bootup and should also contain the core OS stuff. I will partition it for both Windows 7 and Linux but I'm not certain how big I should make both partitions. I was considering going with 60GB for Windows and 20GB for Linux but is that big enough for keeping the core Ubuntu on?

Any other thips and advice for me?

Thanks!

---

### Post by Hedgehog1 on 2011-05-16
Actually your size estimate of 20 gigs for the Ubuntu '/' (root) partitions sounds about right.

You can create a '/home' partition on the HDD, as well as the Swap space on the HDD since you will only use that to sleep/suspend operations.

***The Hedge***

:KS

---

### Post by dino99 on 2011-05-16
windows likes to be installed first
but prepare your hdds to have no more than 3 primary partitions, and make an "extended" partition for all other space, into which you can create the ubuntu partitions

after windows installation, resize its partitions if you need to make room, then follow the help below:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

