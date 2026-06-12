---
title: "Ubuntu 12.04 reinstall problem"
date: 2013-08-10
forum: Installation &amp; Upgrades
---

### Post by mojur on 2013-08-10
I tried to reinstall my ubuntu, but I get this when I run the install cd. I have no idea what to do. Please, help! I need to work, and I do not know what to do.

I had to do this, because when I originally installed ubuntu I made a mistake and installed it twice, creating two partitions of 500 GB on my 1 TB hard disc, and now I ran out of space. I couldn't solve my partiotion problem with the disk manager, and in the ned deleted the unused partition. This did nothing good for solving my problem, so I decided to reinstall.

---

### Post by DeanoCYM on 2013-08-11
I would re-burn your installation CD and try again first

---

### Post by mojur on 2013-08-12
I did that. The new CD was burned at a completly different computer, and I still get kernel panic, only this time with a different code in front of it.

Sorry for the upside-down picture.

---

### Post by DeanoCYM on 2013-08-13
Run [memtest]("http://askubuntu.com/questions/187573/memtest-with-ubuntu-12-04-live-cd") off your live cd to check your RAM is all OK.

Another idea: I had a similar problem when my graphics card died, maybe try and boot your PC without the graphics card plugged in using your onboard graphics to see if thats the problem.

---

