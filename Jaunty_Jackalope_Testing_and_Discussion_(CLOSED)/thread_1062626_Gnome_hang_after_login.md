---
title: "Gnome hang after login"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xens on 2009-02-07
Yesterday's updates killed my gnome :]

I enter my login then gnome display my wallpaper and that's all, nothing more.

I don't know how I can debug this, any idea?

I'm running it on a Dell D630

Xens

---

### Post by Timon&amp;Pumba on 2009-02-07
It is probably the same problem as this thread describes: [http://ubuntuforums.org/showthread.php?t=1061919]("http://ubuntuforums.org/showthread.php?t=1061919").
It is the Compiz - Xserver combination that is the cause of the problem.

---

### Post by xens on 2009-02-07
thanks ;)

dpkg-reconfigure xserver-xorg and it works now ^^

---

### Post by habtool on 2009-02-07
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344/](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344/)

WORKAROUND:
Use xserver-xorg-core 1.5.99.902-0ubuntu1
-OR-
1. Start your session
2. Go to terminal (ctrl+alt+F1) and kill compiz.real via killall compiz.real -s KILL
3. go back to your session (ctrl+alt+F7)
4. remove /dev/nvidiactl (this will be regenerated next time you restart GDM)
5. start compiz

---

