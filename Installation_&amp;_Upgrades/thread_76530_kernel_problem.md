---
title: "kernel problem?"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by marmolro on 2005-10-15
In my last post [http://www.ubuntuforums.org/showthread.php?t=75235]("http://www.ubuntuforums.org/showthread.php?t=75235")  I expose the problem with wheel mouse(the wheel don't work).

After multiples test I think the problem is in the new kernel (2.6.12-9-386). Now i boot with the kernel 2.6.10-5-386 and the wheel works fine :p 

In the newest kernel i try to read mouse events directlly at device (/dev/input/mice, /dev/input/mouse0) and I see all events, except the wheel events, so I supose there is "bug" in the newest drivers.

Marmolro

---

