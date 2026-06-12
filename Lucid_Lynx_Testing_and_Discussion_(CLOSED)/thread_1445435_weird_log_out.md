---
title: "weird log out?"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dbowlin17 on 2010-04-02
I used the force quit icon you can put on a panel just to test it. I forced the tetris game to quit and the computer logged me off... why?

---

### Post by happyhamster on 2010-04-02
It's a warning that you should never stop playing tetris. Or else :p

More seriously, the matter is under investigation. See:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/550218](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/550218)
[http://ubuntuforums.org/showthread.php?t=1440276](http://ubuntuforums.org/showthread.php?t=1440276)

---

### Post by dbowlin17 on 2010-04-02
i never started playing tetris. i just opened up a windows that happened to be tetris to test it out.

---

### Post by happyhamster on 2010-04-02
It's a problem of the tetris application itself, not the Force Quit applet. If any application that's using the latest version of the libclutter library is closed (by any means), the xserver could crash.

---

### Post by dbowlin17 on 2010-04-02
oh. so if i tried it on chrome it should work?

---

