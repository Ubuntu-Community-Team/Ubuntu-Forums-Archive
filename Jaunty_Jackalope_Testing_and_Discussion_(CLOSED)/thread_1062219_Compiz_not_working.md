---
title: "Compiz not working"
date: 2009-02-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bornio on 2009-02-06
Upgrading to Jaunty 9.04 from 8.10 have stopped Compiz from working.
After some research, I have realized that it does in fact, work however, but all I see if a black screen OR/AND my original wallpaper.

After more research, I have isolated the problem to **/dev/nvidiactl**. The very ***existance*** of that folder has stopped Compiz from **rendering** correctly.

Removing / denying permission to that folder indeed fixed my problems, despite some annoying messages about it being missing.

_IF YOU HAVE THIS PROBLEM:_

1. Start your session
2. Go to terminal (ctrl+alt+F1) and kill compiz.real via **killall compiz.real -s KILL**
3. go back to your session (ctrl+alt+F7)
4. remove /dev/nvidiactl (this will be regenerated next time you restart GDM)
5. start compiz

I would love to hear this helped anyone else, especially verifying there is indeed a problem that needs to be fixed, via the bug report here: [https://bugs.launchpad.net/ubuntu/+bug/326363](https://bugs.launchpad.net/ubuntu/+bug/326363)

---

### Post by stovenator on 2009-02-06
See this thread: [http://ubuntuforums.org/showthread.php?t=1061919](http://ubuntuforums.org/showthread.php?t=1061919) and this bug [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/326366](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/326366) for more on this.

---

