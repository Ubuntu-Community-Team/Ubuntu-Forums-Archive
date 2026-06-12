---
title: "Slow compiz Slow kwin effects on kubuntu 9.04"
date: 2009-03-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nowardev on 2009-03-09
SOLVED READING THIS 

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)



I was on debian sid and kde4.2 and compiz was running like a charm
on kubuntu 9.04 it's pretty slow i can't use anymore.

intel 945gm was working nice with 7.04 7.10 8.04 8.10 and with debian with kde4.2 why now i have this sick issue on 9.04? any ideas? i know i know is an alpha..but..

---

### Post by loneowais on 2009-03-31
Same here....

Ubuntu 9.04 Alpha6 (Compiz) worked like a breeze

But Kubuntu Beta (Kwin) is too sluggish.

---

### Post by QwUo173Hy on 2009-03-31
I have the same problem with the same hardware. I'm not sure how to go about reporting this though. All I know is that visual effects are very sluggish.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/342923](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/342923)

---

### Post by Zorael on 2009-03-31
The intel driver is undergoing heavy work, mostly to migrate to DRI2 and kernel modesetting-aware UXA acceleration, as far as I understand. EXA (the currently default acceleration method) performance is suffering as a result of this. As mentioned in that bug report you could manually enable UXA, though you may get instabilities and other weird behaviour that may or may not improve by upgrading your driver, either through manual compilation or ppa additions.

See [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting) and [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa). There's a script at [https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge) that lets you try that ppa's xorg/drm/mesa/<video driver> package combinations in a live session, so to test them out safely you could just boot a live cd/usb from time to time, then run said script and see if things have improved.

Whatwith KMS not being included into Jaunty, I'm not sure what kind of performance to expect until Karmic. Compiling drivers isn't *that* difficult, but still requires some terminal tinkering (and recovery knowhow).

---

### Post by Gnurou on 2009-04-09
After upgrading today, my desktop effects went back to normal. Looks like this has been fixed recently.

---

### Post by nowardev on 2009-04-19
heere is still sucking now

---

### Post by caryb on 2009-04-19
Doesn't work on my Nvidia 185 driver. It stopped working last week.


Cary

---

### Post by Oenologist on 2009-04-19
I experience same sort of problems, very slow kwin, choppy graphics, sluggish effects (for instance Present Windows). I operate Dell Inspiron 1525 with Intel card, upgraded just a few days to Jaunty. 

I decided to give KDE a try, and I must confess that I'm really impressed, but performance issues are really nasty...

It's funny though, having powerful hardware which should definitely be able to guarantee flawless operation I suffer from xorg eating 40-50% of CPU making life worse. 

Ehhh, I hope the fix will be provided soon.

Anybody else feeling like moaning a bit over the crappy driver/xorg, etc? ;)

---

### Post by nowardev on 2009-04-22
SOLVED:

READING THIS 
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

