---
title: "Jaunty alpha5 NVIDIA or GNOME problem with multiple displays"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kakulacis on 2009-03-07
Hallo!

I've upgraded my system from intrepid to jaunty recently and after upgrade I'm having problems with multiple screens setup (displays are set up as separate xscreens), particularly all windows (except menu's) i'm trying to open in second screen opens in first... Can someone acknowledge this and maybe have some workaround?

Thanks and sorry for my English!

---

### Post by kakulacis on 2009-03-08
Bump!

---

### Post by Ng Oon-Ee on 2009-03-09
Same issue here, for me. Not ALL windows behave this way, though, firefox and thunderbird open where they're run from. Some apps do open correctly if open from the terminal (can't remember what now) but simple things like Places->Home folder always open on the wrong screen.

I've tried disabling compiz, thinking it may be a bug with the Window Placement plugin, but no joy, metacity gives the exact same behaviour. Even prefacing the launch with DISPLAY=:0.1 doesn't always give the correct result (nautilus is a bad culprit).

To reproduce, try running:-
```
DISPLAY=:0.1 nautilus
```

Am not sure if this happens with TwinView.

---

### Post by Ng Oon-Ee on 2009-03-13
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783")

Ah, forgot to put up the bug report here.

---

