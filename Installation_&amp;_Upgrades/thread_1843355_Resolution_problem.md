---
title: "Resolution problem"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by SBMN7 on 2011-09-13
Hello guys, i am using kubuntu on my desktop, ubuntu on my laptop. But i found problem in kubuntu. When i set its resolution 1024x768, its run perfectly. But when i trun off computer and start then its resolution auto change to 1600x....! I tried many time to set my best resolution 1024x768, but it will auto change. My monitor is CRT, 17 Inch . Please help

---

### Post by Grenage on 2011-09-13
If you are using an Nvidia card, then you're probably using nvidia-settings to set the res.  Unless you run it as root, the changes won't be persistent.  If you're _not_ using an nvidia card, read on.

While I prefer to use xorg.conf for setting resolutions, I'll list the xrandr way, as that seems to be the current popular method (it does have some advantages).

Now I'm going to assume (shame on me) that since you can set the resolution via the GUI, that the graphical mode already exists.  In which case type this in:

```
xrandr -s 1024x768_60.00
```

If that worked, then you can add the command to a script for boot-time execution:

```
kdesudo kate /etc/kde4/kdm/Xsetup
```

It will ask for a password, then open the file with Kate.  Once there, you simply need to add the command you just used, then save and close.

Reboot and try.

EDIT: Changes made after realzippy's advice (man that made it a shorter post!)

---

### Post by SBMN7 on 2011-09-13
Thank u very much gren age!

---

### Post by realzippy on 2011-09-13
@ grenage

Although
```
gksudo kate /etc/gdm/Init/Default
```
seems to work (?) it should be
```
kdesudo kate /etc/gdm/Init/Default
```

..also wondering about /etc/**gdm** since OP is on KDE

---

### Post by Grenage on 2011-09-13
Fiddlesticks, thank you for pointing that out; can you tell how often I use KDE?  I don't have a KDE install to hand, but would it be */etc/kde4/kdm/Xsetup*?

---

### Post by realzippy on 2011-09-13
@ Grenage

Yes,
```
kdesudo kate /etc/kde4/kdm/Xsetup
```
is correct.
Note that Xsetup is a shell script,so OP
just has to copy xrandr command into it.
Btw,if there is only 1 screen connected,
xrandr -s 1024x768
also works,OP had not to care about if it is CRT-0,DFP,default or whatever.
Edit:
btw,you remember the "story" I told you via pm?
...just noticed you also used × instead of x in post #2:
xrandr --output VGA1 --mode 1024×768
..so I wonder if it really works for SBMN7...normally it can't.

---

### Post by SBMN7 on 2011-09-13
Thanks my both friends!

---

### Post by Grenage on 2011-09-14
> **realzippy said:**
> @ Grenage

Yes,
```
kdesudo kate /etc/kde4/kdm/Xsetup
```
is correct.
Note that Xsetup is a shell script,so OP
just has to copy xrandr command into it.
Btw,if there is only 1 screen connected,
xrandr -s 1024x768
also works,OP had not to care about if it is CRT-0,DFP,default or whatever.
Edit:
btw,you remember the "story" I told you via pm?
...just noticed you also used × instead of x in post #2:
xrandr --output VGA1 --mode 1024×768
..so I wonder if it really works for SBMN7...normally it can't.

Cheers for that, and I do recall it! I always struggle to proof-read my posts; so it's a good job you're here. :)  Nice tip about the port not being required, by the way.

I'm guessing that the OP either manually typed things in, or simply thanked for the replies, and hasn't tried them yet.  I'll modify the first reply.

---

