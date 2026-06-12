---
title: "Latest KDE 4.1 Updates Kill X or KWin?"
date: 2008-08-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tripinva on 2008-08-03
Hello all:

Ran the latest updates that came down on Kubuntu 4.1 development and everything just locked up on me about 5 minutes after the updates finished.  Upon restarting X, the mouse is busy and just spins and spins on a black screen.  Attempting to use "startx" from the command line doesn't work either.

One note though, is that kdm_greeter chews up 100% of the processor during the time that it's sitting there...

- Trip

---

### Post by eris23 on 2008-08-04
This might be related.  I run a lot of kde apps on gnome, and after the last updates none will start (except amarok).  top shows they are taking up cpu time.

---

### Post by nbachiyski on 2008-08-04
I am experiencing it also.

It seems related to [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/247120](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/247120)

Unfortunately, I haven't found a way around it.

---

### Post by RIchard James13 on 2008-08-05
I had a similar problem with X locking up after an update but a reboot of the system fixed this. So is the problem you are having fixed by a reboot or is it permanent?

---

