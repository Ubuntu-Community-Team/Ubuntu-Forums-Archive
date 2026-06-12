---
title: "W Strangeness??"
date: 2008-08-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-08-29
Anyone tried doing a w lately?

nullack@PPP:~$ w
 06:47:14 up 29 min,  3 users,  load average: 0.39, 0.39, 0.40
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
nullack  tty7     :0               06:40   29:05m 19.36s  0.14s x-session-manag
nullack  pts/0    :0.0             06:47    0.00s  0.14s  0.02s w
nullack@PPP:~$ 

Whos the third user? Are people replicating this issue?

---

### Post by mc4100 on 2008-08-29
Just did a fresh install of Alpha 4, no 3rd user:
```
mike@set:~$ w
 22:00:14 up  1:19,  2 users,  load average: 0.79, 1.12, 0.97
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
mike     tty7     :0               20:51    1:19   8:11m  0.26s x-session-manag
mike     pts/0    :0.0             22:00    0.00s  0.14s  0.00s w
mike@set:~$ 
```

---

### Post by Nullack on 2008-08-29
Hmmm thanks time to wipe this install and go fresh

---

### Post by tawmas on 2008-08-29
No rogue third user here either:

```
tawmas@tylke:~$ w
 23:11:54 up 45 min,  2 users,  load average: 0.98, 0.48, 0.28
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
tawmas   tty7     :0               22:27    0.00s  4:31m  0.18s /usr/bin/gnome-session
tawmas   pts/0    :0.0             23:09    0.00s  0.18s  0.02s w
tawmas@tylke:~$ 

```

---

### Post by klange on 2008-08-29
```
[klange oasis-games 08/29  6:00] ~$ w
 18:12:31 up 1 day, 23:52,  1 user,  load average: 0.01, 0.02, 0.00
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
klange   pts/0    acerlaptop.local 17:59    0.00s  0.22s  0.00s w

```
Nobody extra here.

---

### Post by Nullack on 2008-08-29
Thanks all

It seems to be a bug where if you use tty1 and then exit, it will still say theres 3 users on. If you reboot and run w without using a virtual console it will say 2 as expected. Ill report this as an upstream bug.

Prolly time I rebuilt my machine anyway

---

### Post by mc4100 on 2008-08-29
> **Nullack said:**
> Thanks all

It seems to be a bug where if you use tty1 and then exit, it will still say theres 3 users on. If you reboot and run w without using a virtual console it will say 2 as expected. Ill report this as an upstream bug.

Prolly time I rebuilt my machine anyway
Confirmed, I see it too after a CTRL+ALT F1 and "exit", ...
```
mike@set:~$ w
 01:18:10 up  1:53,  3 users,  load average: 1.23, 1.13, 1.10
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
mike     tty7     :0               23:28    1:53  10:40m  0.22s x-session-manag
mike     pts/0    :0.0             01:18    0.00s  0.16s  0.00s w
mike@set:~$ 

```

---

