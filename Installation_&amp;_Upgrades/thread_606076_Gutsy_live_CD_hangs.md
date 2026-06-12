---
title: "Gutsy live CD hangs"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by lamadredelsapo on 2007-11-07
I'm trying to load Gutsy Live CD (x64 Desktop version) but the problem is it just hangs before showing the desktop. No error messages. It won't show any graphical interface, it just shows a blank screen. My monitor shows a message saying "out of range" just before gutsy hangs, my computer specs are described below.

Any ideas?

---

### Post by dabl on 2007-11-07
The problem is almost certainly that ATI video chip.  Search on it -- probably there is a "boot option" that you can select that will allow the GUI to be presented.  :)

---

### Post by blegmar on 2007-11-07
I'm having the same issues. with the 7.10 desktop x64 install disk. I'm going to try the 32bit disk tonight when I get home.
vid card: nvidia 8800gtx
amd 3800+ x2 (socket 939)
ecs crap mobo
western digital drives
2GB RAM

When I select start from the live cd, it hangs on a blank screen. Same with any other options on that cd.

---

### Post by dabl on 2007-11-07
> **blegmar said:**
> 

 I'm going to try the 32bit disk tonight when I get home.



OK, but that's not the problem ...

> 

vid card: nvidia 8800gtx



THAT'S the problem.  If you can download the Envy script installer, install it, and run it in text mode, it should put a driver in for you.
```

sudo envy -t
```

---

### Post by dave61430 on 2007-11-07
I keep hearing about envy, must find out what it is.
Fixed same problem on my son's machine, problem 16895 here:
[https://answers.launchpad.net/ubuntu/+questions?start=300&batch=75](https://answers.launchpad.net/ubuntu/+questions?start=300&batch=75)

Dave Cohen

---

### Post by lamadredelsapo on 2007-11-09
Will it help to use alternate cd, instead of desktop?

---

### Post by lamadredelsapo on 2007-11-11
It's quite strange because i was able to boot from the 6.10 cd.

---

### Post by lamadredelsapo on 2007-11-11
I've tried to force Ubuntu Gutsy to use a resolution of 1024x768x32 while booting from the CD, the problem is that itnstead of that it tries to use a resolution above 1280x1024x32, which is the max resolution my screen supports. Is there any option to force ubuntu to use a lesser res option while booting from the Ubuntu Gutsy Desktop CD?

---

