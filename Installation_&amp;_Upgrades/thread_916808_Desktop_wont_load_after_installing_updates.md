---
title: "Desktop wont load after installing updates"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by GyronMkwebo on 2008-09-11
I used the update manager to install updates on my HP nx7400 laptop (running Ubuntu 7.10), after which the system requested a restart. I restarted the machine and when it comes time for it to get me to the GUI log in screen, the system just flicks and flicks, then remains in the black screen.
I can see that the system is not frozen because <Ctrl><Alt>F2 takes me to the terminal and i can log-in with no problem at all.I tried to run:
```

sudo dpkg-reconfigure xerver-xorg

```
and after selecting the screen resolution it comes up with, and restarting with:
```

sudo shutdown -r now

```
The problem still persists!
What can i do to re-solve this issue? Also, when comitting the updates, the system showed that it had had issues with mysqlserver package. And when executing the shutdown command, it takes time on 'Stopping Gnome display manager' and also shows a fail in stopping mysql

---

