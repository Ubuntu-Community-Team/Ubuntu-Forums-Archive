---
title: "[intrepid] Terminals have disappeared with the new kernel"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by badp on 2008-09-20
Since the update to the .27 kernel, pressing Ctrl-Alt-F1 shows only a blinking cursor. Same goes for Ctrl-Alt-F2 through Ctrl-Alt-F6. 

Pressing button does nothing. Boot messages are not displayed.

I've idled from some time in #ubuntu+1 and read no reports about it, so I guess this is just a problem with my system.

Suggestions?

---

### Post by spiderbatdad on 2008-09-20
My intrepid is working excellently 2.6.27-3. Perhaps read your dmesg, maybe a hardware issue like not properly detecting keyboard.

---

### Post by badp on 2008-09-20
Could the following be related?

```
[    4.146310] uvesafb: failed to execute /sbin/v86d
[    4.146314] uvesafb: make sure that the v86d helper is installed and executable
[    4.146335] uvesafb: Getting VBE info block failed (eax=0x4f00, err=-2)
[    4.146338] uvesafb: vbe_init() failed with -22
[    4.146345] uvesafb: probe of uvesafb.0 failed with error -22

```

---

### Post by spiderbatdad on 2008-09-20
I believe it could be related. V86d is a daemon that has something to do with virtual resolutions among other things.

---

### Post by badp on 2008-09-20
That did the trick. Thank you.

Oh. I'm sorry for posting this in the wrong forum.

---

