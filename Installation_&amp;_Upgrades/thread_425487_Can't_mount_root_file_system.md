---
title: "Can't mount root file system"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by theGasman on 2007-04-27
Hi,

This is my very first attempt at Linux after over 20 years computing and I'm not having any success.
I can't even boot the installer routine on my system!
I've tried both the current Ubuntu releases (6 and 7), and both give the same problem  - they hang as the kernel loads when I boot from the install CD. The last things I see if I turn quiet and splash off is "Mounting root file system" which hangs, and I get dropped back to the comand prompt. I have also seen cannot load tty" whatever that means. Can anyone help me here?"

I have suspected a problem with recognizing my hard disks, and have tried booting with only the DVD drive connected, but same problem.
Asus P5BE plus, E4300, 2Gb RAM.

TIA,

Martin

---

### Post by eapache on 2007-04-27
Try running the cd verification.

---

### Post by theGasman on 2007-04-27
I have now read some more posts on this forum and see that mine is a common problem, with the following error message:
> /bin/sh: can't access tty; job control turned off 

This is continued with the following:
> After reading the MANY replies and posts in this thread so far, it's clear that the error message in the subject line can occur for MANY different specific reasons. What all of these reasons seem to have in common is that the new 2.6.20-15 kernel used by Fiesty chokes when it encounters hardware or combinations of hardware that its boot-up routines aren't coded to handle properly. When it chokes, it almost always spits out that error message at the end. Solving your particular issue or finding a workaround for it may require a lot of time and patience, if you ever solve it all.

Well no thank you! I was trying Linux to hopefully get away from all that nonesense. At least windows boots (normally). Hang on Bill, I'm coming baaack....

Martin

---

