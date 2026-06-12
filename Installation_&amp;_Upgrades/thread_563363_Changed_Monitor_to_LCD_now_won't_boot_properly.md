---
title: "Changed Monitor to LCD now won't boot properly"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by TheShadows on 2007-09-29
Hey I just changed monitor from a CRT to a NEC LCD ( Model: LCD52V ) and now i'm having problems when booting.

---

### Post by Pumalite on 2007-09-29
[http://ubuntuforums.org/showthread.php?p=2221097](http://ubuntuforums.org/showthread.php?p=2221097)
[http://ubuntuforums.org/showthread.php?t=563126](http://ubuntuforums.org/showthread.php?t=563126)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/97026](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/97026)
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/81206](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/81206)
[http://www.cyberciti.biz/tips/new-19-viewsonic-widescreen-lcd-monitor.html](http://www.cyberciti.biz/tips/new-19-viewsonic-widescreen-lcd-monitor.html)

---

### Post by TheShadows on 2007-09-29
Went to links you provided and, the Bugs links dont' show me any info. The link to the 19" LCD 2nd link from bottom takes me to a review page no help there. And the rest yea similar.

---

### Post by Pumalite on 2007-09-29
I'll think about it.

---

### Post by Pumalite on 2007-09-29
What's the error message?

---

### Post by TheShadows on 2007-09-29
I see. Hmm, I have been able to get booted into the live cd to change stuff. So i'm trying again.

---

### Post by Pumalite on 2007-09-29
Post back if you encounter difficulties.

---

### Post by TheShadows on 2007-09-29
Did enable the nividia driver. Which isn't affecting things. But since the monitor change i'm gettin the black screen after the boot process after the GRUB screen.

---

### Post by ryanVickers on 2007-09-29
reconfigure the xserver:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by TheShadows on 2007-09-30
I did
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

Booted, then after the Ubuntu loading screen, I recieved the black screen.

---

### Post by ryanVickers on 2007-09-30
Very strange!

I changed my **motherboard** and that was all I needed to get everything totally back to normal!! :p  Try *that* on windows! ;)

---

### Post by TheShadows on 2007-09-30
i have been also recieving this on loading after the Ubuntu load screen:

udevd-event[1906]: run_program: '/sbin/modprobe' abnormal exit

---

