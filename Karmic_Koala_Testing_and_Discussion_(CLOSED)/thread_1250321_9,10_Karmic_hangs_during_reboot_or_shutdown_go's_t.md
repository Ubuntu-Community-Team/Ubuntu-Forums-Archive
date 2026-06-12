---
title: "9,10 Karmic hangs during reboot or shutdown go's to black screen"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2009-08-26
Installed 9.10 in Vista dual boot 3 times. Hangs during reboot or shutdown go's to black screen. 9.04 works fine.  64 bit user.

---

### Post by Yellow Pasque on 2009-08-27
With the most recent updates, my Karmic64 install was also hanging on shutdown/reboot :\ .
I thought it was because of the experimental video driver stuff I've been pulling from git branches, but maybe not. I'm going to give it a few days, and if it's not fixed the next time I boot that install and update it, I'll start troubleshooting it.

---

### Post by dearingj on 2009-08-27
I'm also experiencing this problem. The weirdest thing is that it's not consistent: Sometimes, very rarely, my computer will shut down or reboot like it's supposed to. Please post here if you find a solution.

---

### Post by Yellow Pasque on 2009-08-27
[https://bugs.launchpad.net/bugs/418509](https://bugs.launchpad.net/bugs/418509)

---

### Post by garvinrick4 on 2009-08-28
Thanks for reply's if anyone finds a fix or Ubuntu fix's please post here. I am
now back to 9.04 and still tempted to upgrade one more time to 9.10. I enjoy
working with the Alpha's to help out where I can. Am thinking about getting a 
laptop to just use with new distro's so will not have any WUBI problems. Never had
one this one seems like GRUB  but being in folder in Windows uses DOS GRUB. But
as I understand Alpha 4 has a change in its GRUB!!!  For minds greater than mine. 
Sure they will find a fix soon. Find myself hooked on Linux wish I would have looked into
these Forums long ago.

---

### Post by garvinrick4 on 2009-08-28
Aug 27 2009 10:58 pm PST  using WUBI dual boot with Vista shutdown or reboots fine.
 4th time was a charm.

---

### Post by P.KO on 2009-08-29
Hi,

Seems that kernel 2.6.31-8 has resolved the issue.

---

