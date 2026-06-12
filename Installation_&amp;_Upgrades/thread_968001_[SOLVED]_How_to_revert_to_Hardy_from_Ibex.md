---
title: "[SOLVED] How to revert to Hardy from Ibex"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by AlanInVancouverBC on 2008-11-02
For the present, I've given up on Ibex, mainly around the internet connection fiasco.
What is the safest way to revert to Hardy?

---

### Post by XDevHald on 2008-11-02
Did you upgrade to Ibex from hardy?

When you are booting your computer at start up, and it is counting down to start the boot splash, hit ESC and tell us if you still have 8.04 in the GRUB menu along with 8.10, if you do then you need to see this post: [http://ubuntuforums.org/showthread.php?t=967797](http://ubuntuforums.org/showthread.php?t=967797)

---

### Post by AlanInVancouverBC on 2008-11-02
Just 8.10

---

### Post by XDevHald on 2008-11-02
Only solution here is to download and burn an ISO to a blank CD. You can get'em at walmart, best buy, target etc.

Get that beta off and do something good with Ubuntu :) psstt! get Hard Heron ;)

[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) <-- check left menu, I would recommend getting a FREE CD of Hardy and it will take up to 4-6 weeks, mine took 1 week so you might get lucky.

Enjoy!

---

### Post by magnus0 on 2008-11-02
You could make a new partition and move your home folder there and then do a clean hardy install on the other partition. While installing, select the partition you just made as /home partition.

---

### Post by AlanInVancouverBC on 2008-11-23
In the end, I just searched which WUBI to use for 64-bit 8.04.1 Ubuntu and downloaded it and installed it. Of course, unlike 8.10, internet worked right away, graphics worked right away (my 2 main problems). I'll wait for others to experiment with later releases, like 9.04 (Jackalope?) rather than download install and freak on the first day, prior to learning that a distro is so buggy!

---

### Post by merlin666 on 2008-12-05
> **Steven Myers said:**
> Did you upgrade to Ibex from hardy?

When you are booting your computer at start up, and it is counting down to start the boot splash, hit ESC and tell us if you still have 8.04 in the GRUB menu along with 8.10, if you do then you need to see this post: [http://ubuntuforums.org/showthread.php?t=967797](http://ubuntuforums.org/showthread.php?t=967797)

I have several Kernel options in the boot menu, but no choice between 8.04 and 8.10. Also I commented out the older 8.04 kernels, which was quite difficult without arrow keys (lacking in 8.10). I doubt that booting to an old kernel will bring back 8.04 ... so please explain your thought.

---

