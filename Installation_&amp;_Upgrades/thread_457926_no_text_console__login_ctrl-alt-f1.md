---
title: "no text console / login ctrl-alt-f1"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by almark on 2007-05-29
Hi just upgraded to Feisty yesterday. Text console / login is missing when I ctrl-alt-f1 Is this a bug or a new feature?

Regards
Mark

---

### Post by Blender on 2007-05-29
It's definitely not a bug, i.e. it works on my two machines (one upgraded from Edgy, the other with a fresh Feisty).

---

### Post by almark on 2007-05-29
Very weird problem, the tty files in /etc/event.d were damaged like below

/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1 
 

exec /sbin/getty 38400 tty1

---

### Post by Blender on 2007-05-29
Weird, indeed.

Did you manage to fix it or are you still experiencing the problem?

The only thing I can think of is reinstalling the **system-services** package, which should recreate those files:
```

[~] $ dpkg --search /etc/event.d/tty1 
system-services: /etc/event.d/tty1
[~] $ sudo apt-get --reinstall install system-services

```

---

### Post by almark on 2007-05-30
I fixed the problem manually by changing the existing faulty line /sbin/getty 38400 tty1exec /sbin/getty 38400 tty1 to exec /sbin/getty 38400 tty1 The problem was described in launchpad and was supposed to be fixed...

Cheers
Mark

---

### Post by gauss on 2008-06-24
> **almark said:**
> Hi just upgraded to Feisty yesterday. Text console / login is missing when I ctrl-alt-f1 Is this a bug or a new feature?


I have the same problem after I upgraded to Heron. I checked [FONT="Courier New"]/etc/event.d[/FONT] and it looked OK. I'm running KDE with a Microsoft Ergonomic Keyboard 4000. Every other keystroke works fine.

Could KDE be somehow capturing Ctrl-Alt for its own purposes? Could the driver be faulty? (I ran it under Gibbon without this problem.) Any hints as to where to look would be gratefully appreciated.

[SOLVED] My problem was my keyboard. It needed an "F Lock" key depressed to access the F-keys.

---

