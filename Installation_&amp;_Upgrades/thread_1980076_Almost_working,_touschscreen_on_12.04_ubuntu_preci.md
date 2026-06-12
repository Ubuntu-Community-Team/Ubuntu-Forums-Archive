---
title: "Almost working, touschscreen on 12.04 ubuntu precise"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by deport on 2012-05-14
Moving a finger across the screen is showing characters when monitoring with cat.  

First how it doesn't work:
I excpected the command 
   sudo cat /dev/ttyS4
to cause random characters to appear as an interpretation of the data stream when moving fingers across the screen.  Instead I'm getting "Device or resource busy"

Not sure why, the touchscreen doesn't load as ttyS4, but using dmesg shows it is mounted at tty/ttys$/serio1/input/input4

What does work is 
  sudo cat /dev/input/event4

It works as far as showing random looking characters as a finger is drawn across the screen.  However, the mouse pointer doesn't move.  It's good to know that Ubuntu can see the touchscreen and data is being sent.


**How do I finish configuring ubuntu for this device?**

---

### Post by deport on 2012-05-18
> **deport said:**
> Moving a finger across the screen is showing characters when monitoring with cat.  

First how it doesn't work:
I excpected the command 
   sudo cat /dev/ttyS4
to cause random characters to appear as an interpretation of the data stream when moving fingers across the screen.  Instead I'm getting "Device or resource busy"

Not sure why, the touchscreen doesn't load as ttyS4, but using dmesg shows it is mounted at tty/ttys$/serio1/input/input4

What does work is 
  sudo cat /dev/input/event4

It works as far as showing random looking characters as a finger is drawn across the screen.  However, the mouse pointer doesn't move.  It's good to know that Ubuntu can see the touchscreen and data is being sent.


**How do I finish configuring ubuntu for this device?**

It is also working /dev/input/mouse1

mouse0 is the regular mouse.

The touchscreen[FONT=Arial][SIZE=2][/SIZE][/FONT] "works", sending info via cat.  But it is as if X does not know that there is a touchscreen.

---

### Post by deport on 2012-05-18
marked thread as solved.  Posted in wrong forum.

---

