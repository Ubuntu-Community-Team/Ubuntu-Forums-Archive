---
title: "Compiz.real 90%CPU/memory hog"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Skipnaz on 2009-10-18
After booting everything is slow. Compiz.real uses 80~90 CPU . The memory it uses just keeps ticking upward. Visual Effects is in Normal on every start, when I change it to None Gnome desktop speeds up. When I change it back to Normal it works good. So it seems its only on the bootup. It always reverts to Normal and won't save my setting to None when I reboot.  This just started the last couple of days. Does this seem to be a bug or maybe I have something corrupted. Compiz 0.8.4-Oubuntu1, Karmic 2.6.31-14-generic

---

### Post by dpc.ucore.info on 2009-10-20
Same here.

---

### Post by NCLI on 2009-10-20
Skipnaz, please report a bug ;)

Run: "ubuntu-bug compiz" in either Alt+F2 or a terminal.

---

### Post by Skipnaz on 2009-10-20
I go to Users and Groups and make another user I don't have this problem

Thanks NCLI for the code to help me file a report

---

### Post by dpc.ucore.info on 2009-10-21
Any bugid?

---

### Post by Skipnaz on 2009-10-21
This is the Bug ID
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/456374](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/456374)

---

### Post by dpc.ucore.info on 2009-10-23
In the shell:

```
$ find ~ -type d | grep compi
```

And remove everything that comes across and is not your personal file. This helped on my box.

I've done this when logged of and switched with Alt + F1 to plain console to make sure nothing will be saved when logging off from the graphical session. But I'm pretty sure this is not required.

---

### Post by Skipnaz on 2009-10-23
I been having problem with my box not booting. Its been on and off for a while. It been crashing as soon as the OS starts to load. Somtimes I need to press the reset button half a dozen times before it takes, other times it does it on the first time. In my bios I have a option where a voice tells me what is wrong when boot fails. The ladies voice says "system failed due to system over clocking" but this old processor is locked. If I hadn't had that voice there to tell me boot failed I'd be looking at a black screen waiting for it to load, so thats kinda neat.
I since formated and installed 9.10rc and checking it out. I think it might be hardware starting to fail. Also my onboard NIC stopped working. I was watching the light on the back of the box and it was on until the OS started to load and then it went off. I put in a old PCI NIC card and it works. After testing in a week Im going to try an older OS and see if it still acts up. I tried the strace -p... and it made a file that was empty. Thanks you for the help

---

