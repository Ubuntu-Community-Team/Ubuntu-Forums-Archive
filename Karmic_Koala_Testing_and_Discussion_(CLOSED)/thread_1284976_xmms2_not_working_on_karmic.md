---
title: "xmms2 not working on karmic"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tijuana on 2009-10-07
Just today I installed beta 2 of karmic x64 on my laptop to test it and see if I could help out some. I've already encountered a problem: xmms2d won't start. Here's the message thrown by the terminal.

```
nico@nico-laptop:~$ xmms2d
 INFO: ../src/xmms/log.c:49: Initialized logging system :)
09:08:15 ERROR: ../src/xmms/ipc.c:783: Couldn't setup IPC listening on 'unix:///tmp/xmms-ipc-nico'.
09:08:15 FATAL: ../src/xmms/main.c:494: IPC failed to init!
nico@nico-laptop:~$ 

```

It's probably due to me being a newbie or this being a beta or the x64 version (or all three combined), but since I can't make heads nor tails of the message I'm asking you guys for some advice

Thanks!

---

### Post by tijuana on 2009-10-07
bump

---

### Post by Nosferax on 2009-10-13
> This occurs when a user attempts to restart xmms2d and another user has it already started. Login as root, issue "killall xmms2d", relogin as your user and issue "xmms2d &"

[http://www.linuxquestions.org/questions/linux-software-2/unique-xmms2-problem-443207/](http://www.linuxquestions.org/questions/linux-software-2/unique-xmms2-problem-443207/)

---

