---
title: "Ubuntu 10.10 64-bit Authentication Failure"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Joseph Schwenker on 2010-10-10
When I try to boot from the Ubuntu 10.10 64-bit live CD, I get to the purple screen with the five dots, and the dots light up for a while, but then the screen goes to a terminal with AUTHENTICATION FAILURE written down the screen.  What should I do?  I have booted to live CDs successfully before, though this is my first time booting from a 64-bit one, as I just upgraded my processor.

---

### Post by Joseph Schwenker on 2010-10-10
If it helps, my processor is a [Pentium Wolfdale 2.7 64-bit]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116076&cm_re=pentium_775-_-19-116-076-_-Product").
I noticed that the iso says "amd64", but my processor is Intel, not AMD.  I ran this on a computer with an AMD 64-bit processor, and it worked beautifully.

---

### Post by itten on 2010-10-10
The same thing.
After i had 'Authentication Failure' strings down the screen i get login screen, but i don't have any login and password yet. I used "Startup disk creator" to make bootable USB.

---

### Post by DIInversion on 2010-10-11
I had the same error running on an i7 processor. I seemed to fix it by burning another disk in k3b (I used Brasero before) and then, at the accessibility prompt when booting the disk (the little man and the keyboard icon) pressing a key and then selecting, "Try Ubuntu without Installing". This got me past the plymouth screen and into a desktop where I then installed it.

It's kind of annoying it wasted a disk but that's what got 10.10 on my laptop. :D

---

### Post by Joseph Schwenker on 2010-10-11
I solved this by using the alternate installation disc.  I assume the the previous poster's option should also work.

---

