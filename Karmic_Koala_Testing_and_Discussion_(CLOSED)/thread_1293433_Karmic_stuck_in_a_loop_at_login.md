---
title: "Karmic stuck in a loop at login"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by K7AAY on 2009-10-17
Karmic boots, prompts for my password, then blincks, clears the screen, and again prompts for my password. How might I look into what causes this?  Worked fine for about a week, with the only prior problem random lockups (solved today by doubling the RAM to 1GB in my HP Paviliaon xe2113us, which survived four passes through MEMTEST).

Thank you, all, for your attention to this problem.

---

### Post by louieb on 2009-10-17
Have you been using** sudo **when you should be using **gksudo** for graphical apps?
That can cause problems with xorg. Check the owner of ~/.Xauthority - change it back to you if its not.

---

### Post by lovinglinux on 2009-10-17
Karmic related questions are better placed at [Karmic Koala Testing and Discussion](http://ubuntuforums.org/forumdisplay.php?f=359).

---

### Post by K7AAY on 2009-10-17
> **louieb said:**
> Have you been using** sudo **when you should be using **gksudo** for graphical apps?
That can cause problems with xorg. Check the owner of ~/.Xauthority - change it back to you if its not.


1) I went to Recovery Mode through GRUB, but could not find .Xauthority in my root nor my /home/k7aay directory. There's only one user on ths machine, k7aay.

2) Thread moved to 
[http://ubuntuforums.org/showthread.php?p=8120248#post8120248](http://ubuntuforums.org/showthread.php?p=8120248#post8120248)

3) louieb , thank you!

---

