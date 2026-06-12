---
title: "Ubuntu destroyed windows boot sector"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by nico21 on 2005-11-23
I tried installing Hoary a couple of month ago, everything was fine as long as I didn't mount the windows partition during the installation. When I did so, I got thi:

"WINDOWSSYSTEM32CONFIGSYSTEM.log is 1k, but it has 228 clusters (1824 k) error."

...and windows boot sector was erased so grub couldn't find it.

I downloaded breezy recently and the same message occurs. I didn't go any further in order not to have the same result.

What's the problem exactly?

---

### Post by yesplease on 2005-11-23
Why did you mount the windows partition during install? To resize it? 
Did you get this message during install?

---

### Post by nico21 on 2005-11-23
[QUOTE=yesplease]Why did you mount the windows partition during install? To resize it? 
Did you get this message during install?[/QUOTE]

I mount it because I didn't want to do it after installation. I prefered to do this directly.:smile: 

The probleme is that with breezy the default configuration (when you want to partition manually I precise) is so that the windows partition is mounted and not amorcable (my second fat 32 partition for sharing file is also mounted but amorcable* which is bizarre).
Whith hoary the default option was that nothing was nor mounted or amorcable*...

Yes, I got the message during the install.
Does it mean that my windows boot sector is too fat(:rolleyes: ) and that ubuntu can't handle it?

I don't want to make stupid error anymore so if somebody could tell me the exact way to avoid problems (I just want to mount my second fat32 partition)
The problem is that (as I said) the default option in the manual partitioning already modifies my main windows partition (not amorcable*) .


***: I don't know the translation for the french term amorcable

---

### Post by yesplease on 2005-11-23
During install you wiil arrive at partitioning. Choose manual partitioning en mount the partitions for ubuntu, not for windows. You mount them by selecting the partitions, go to a list and fill in the right properties.  Do not install if you cant figure out how to mount, but come back here.

I hope  this helps, but perhaps I misunderstood your problem.

---

