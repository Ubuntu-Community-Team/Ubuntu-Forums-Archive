---
title: "[SOLVED] Thinkpad trackpoint middle button scrolling"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by machoo02 on 2008-10-09
In prior releases, middle button scrolling with a trackpoint could be configured via options in xorg.conf.  With Intrepid's switch to .fdi based input configuration for X, how can I enable middle button scrolling again?  Does anyone have an .fdi file already?  Running Kubuntu Intrepid on a Thinkpad R52, btw.

---

### Post by machoo02 on 2008-10-09
Ok...I figured out how to enable it via xinput:
```

xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation Button" 8 2

```
So now the questions is: how do I structure the .fdi file to have this option enabled permanently?   I've looked over [X configuration wiki page]("https://wiki.ubuntu.com/X/Config"), but I haven't been able to get a working .fdi file yet.

EDIT:
Solved via [this post]("http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/") on Michael Vogt's blog.

---

