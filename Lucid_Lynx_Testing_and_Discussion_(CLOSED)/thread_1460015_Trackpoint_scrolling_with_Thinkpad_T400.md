---
title: "Trackpoint scrolling with Thinkpad T400"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by john_brown_jr on 2010-04-22
Hi folks,

I am testing Lucid Beta (with all updates as of April 22), and I can not seem to figure out how to enable trackpoint scrolling on my Thinkpad T400. With trackpoint scrolling I mean that the scrolling should happen when I hold down the middle button for trackpoint and move trackpoint at the same time.

In 9.04 I did it with a HAL policy file, but now that HAL is gone, i guessed that it won't work anymore. I tried to do this with UDEV rule (/etc/udev/rules.d/99_trackpoint.rule)

```
ACTION!="add|change", GOTO="xorg_trackpoint_end"
KERNEL!="event*", GOTO="xorg_trackpoint_end"

ENV{ID_PATH}!="platform-i8042-serio-1", GOTO="xorg_trackpoint_end"

ENV{x11_options.EmulateWheel}="1"
ENV{x11_options.EmulateWheelButton}="2"
ENV{x11_options.XAxisMapping}="6 7"
ENV{x11_options.Emulate3Buttons}="0"

LABEL="xorg_trackpoint_end"
```

However, this does not seem to help. Anyone has any ideas why?

---

### Post by Ub1476 on 2010-04-22
Maybe [this]("http://psung.blogspot.com/2010/04/thinkpad-trackpoint-scrolling-in-ubuntu.html") works.

---

### Post by john_brown_jr on 2010-04-22
It works indeed. Thanks!

---

