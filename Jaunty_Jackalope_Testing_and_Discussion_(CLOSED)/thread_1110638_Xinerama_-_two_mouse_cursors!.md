---
title: "Xinerama - two mouse cursors!"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by azredwing on 2009-03-30
Hi all,

I just upgraded to Jaunty. I have a dual-screen setup with an nVidia GeForce 8600, non-free drivers. I'm using Xinerama.

When I move my cursor from one screen to the other, the cursor simultaneously stays on the first screen and begins moving normally on the other screen. The cursor basically sits in the last place it was at before I moved the mouse to the other screen.

Oddly, when I take a screenshot to show the two cursors side-by-side, the one on the inactive monitor disappears (in the screenshot, not on the monitor)

Dunno if I need to file a bug report on this or what. Anyone encounter this?

---

### Post by |Porsche on 2009-03-30
What happens on TwinView?

---

### Post by azredwing on 2009-03-30
> **|Porsche said:**
> What happens on TwinView?

TwinView works fine. I switched to Xinerama because for some reason on TwinView, I couldn't add another panel to the secondary monitor. I think TwinView spans both monitors but recognizes them as one super-monitor. That said, I couldn't drag-and-drop a panel from one monitor to another, nor could I place it directly using gconf-editor.

---

### Post by canabal on 2009-03-30
I am having the same problem.

Does not really bother me, but should be fixed regardless.

---

### Post by |Porsche on 2009-03-30
Thats weird. I have no problem on either Xinerama or TwinView. So far I don't see a difference between the two, they do the same thing, for the only exception that TwinView doesn't make my conky flicker.

What driver are you using? I am using 180.29.

---

### Post by James_Lochhead on 2009-03-30
Save problem here, except I am using separate X screens. I actually quite like it though.

---

### Post by lime4x4 on 2009-03-30
same here using 4 lcd panels each as a seperate x-screen

---

### Post by azredwing on 2009-03-30
> **|Porsche said:**
> Thats weird. I have no problem on either Xinerama or TwinView. So far I don't see a difference between the two, they do the same thing, for the only exception that TwinView doesn't make my conky flicker.

What driver are you using? I am using 180.29.

180.37. I can try rolling back; not sure how I would do that though at this instant. I probably won't get around to that until this evening.

---

### Post by excentric on 2009-04-09
Just upgraded to jaunty. Same problem...

---

### Post by d2globalinc on 2009-04-10
Same issue here - Jaunty 64bit Beta w/ latest updates 180.44 Nvidia Driver - 3x Nvidia Geforce 8800GTX's - all screens joined by xinerama have this issue of a duplicate mouse cursor being left behind when you transition the mouse to another monitor.. 

Found a Bug report here:  [https://bugs.launchpad.net/ubuntu/+bug/357901](https://bugs.launchpad.net/ubuntu/+bug/357901)

Add your comments if you have the same issue so this gets attention!

Thanks!

Shane Menshik
D2 GLOBAL INC
[http://www.d2global.com](http://www.d2global.com)

---

### Post by azredwing on 2009-04-10
The 180.44 update didn't solve the situation. I ended up switching to TwinView (got panels on both monitors now) but I'll keep checking out the situation.

---

### Post by TheGolfball on 2009-04-22
I'm using 9.04 RC.  I have the same problem with Xinerama.  One mouse pointer per monitor when desktop is stretched accross both displays.  Looks tacky.

---

