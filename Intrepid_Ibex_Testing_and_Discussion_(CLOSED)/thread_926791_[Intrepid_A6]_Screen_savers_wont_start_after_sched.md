---
title: "[Intrepid A6] Screen savers wont start after scheduled idle time"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ju2wheels on 2008-09-22
Hi everyone, im at a loss here, I really cant figure out why my screen savers wont kick in when ive been Idle for the scheduled amount of time. Ive checked my system logs and cant find any errors. The screen saver looks like its about to start and then it appears to just crash and never load. However, when I use the screen saver panel to select a screen saver, I can see the previews fine and even make them full screen.

Any ideas?

---

### Post by Elfy on 2008-09-22
There are a few things to try, there is apparently a bug in it atm - check them out. Is it the same issue?

[http://ubuntuforums.org/showthread.php?t=885023&highlight=screensaver](http://ubuntuforums.org/showthread.php?t=885023&highlight=screensaver)

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/256586/](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/256586/)

---

### Post by ju2wheels on 2008-09-22
Thank you very much, that indeed was the problem. The workaround fixed it for me too thanks.

FYI for anyone who catches this thread and has screen saver problems its related to compiz:

Compiz Settings Manager-> General Tab-> General Options -> Uncheck  "Unredirect Fullscreen Windows"

I think this issue manifests itself in other ways as well. When I was playing OpenArena, I was forced out of fullscreen mode and it went into a windowed mode where it would not release my mouse. I would then have to switch to a tty console to terminate OpenArena and log out of my graphical session to regain control of my mouse.

---

