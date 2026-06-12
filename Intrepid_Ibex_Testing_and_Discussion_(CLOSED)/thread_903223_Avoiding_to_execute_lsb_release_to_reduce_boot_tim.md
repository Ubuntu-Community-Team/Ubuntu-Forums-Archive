---
title: "Avoiding to execute lsb_release to reduce boot time"
date: 2008-08-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by klim8 on 2008-08-28
Using bootchart I have found that lsb_release is called twice (in my current system, maybe other packages are also affected) during the boot up process. It takes a lot of time since it uses apt-cache in order to figure out the distribution name, version etc. that are needed by some scripts (update-grub, for example).

I have opened a bug in order to replace the calls to lsb_release with calls to less CPU and IO intensive commands. We should identify the packages that are using it, specially if they are used in the boot up process.

Please, confirm the bug. And add new offender packages that use lsb_release if you find them.

[https://bugs.launchpad.net/ubuntu/+bug/262050](https://bugs.launchpad.net/ubuntu/+bug/262050)

---

### Post by klim8 on 2008-08-28
I forgot to say that I have shaved 5 seconds off the boot time by avoiding 1 execution of lsb_release. 5 seconds out of 55 is almost a 10% reduction.

---

