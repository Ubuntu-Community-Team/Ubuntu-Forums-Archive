---
title: "Fresh 11.04 install on Mini 110 SLOW SLOW SLOW"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by Capt_Lou on 2011-09-27
Hello:
Ubuntu newbie here.
Just completed a fresh installation of 11.04 on an HP Mini 110.
Having an number of issues, webcam, Wifi which I expect are just driver issues and I will get to. 
My main concern is a performance issue. The OS seems drastically SLOW. Seems to boot in a reasonable manner, although slower than XP, however, launching apps, like Banshee for example takes 45s to 1 min. Being new to Ubuntu, I toured through some of the utilities and went through the system checker, passing most tests. The utility that shows real time processor utilization is showing CPU 0 and CPU 1 running at 100%, with no other apps running.
This can't be normal. Any ideas?
Thanks,
Lou

---

### Post by ajgreeny on 2011-09-27
No, it certainly is not normal.

Open a terminal and type ```
top
``` to see what is using all the cpu%.  It should show the processes running with the high cpu% at the top of the list, so may give some clue.

Have you tried logging in to the classic desktop to see if that makes any difference?

---

### Post by 2F4U on 2011-09-27
You may want to consider switching to a more lightweigth desktop environment such as XFCE or LXDE. I have both running on two older machines and I am very satisfied with the performance.

---

