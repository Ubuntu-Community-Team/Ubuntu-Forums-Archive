---
title: "Ubuntu 8.10 questions"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by duruttye on 2008-10-12
Have a few questions regarding this new 8.10 version of our favorite OS.
I had to try it out, because v.8.04 didn't work out for me at all, and I broke my old 7.10 version when wanted to plug in a second monitor.
I'm using a dell inspiron 1501

So, here goes:

No restricted driver for the video card, or very low performance. Not sure which... Ex.:scrolling down a simple web page (no flash, or java) uses up a lot of the CPU-s time, and it looks ugly. In hardware drivers (restricted drivers menu - I think) I have a "wl" driver, but I have no idea what that is... I have wireless, too, in the 7.10 version I had a restricted driver for that, too, now I use ndiwrapper.
Can't change the keyboard layout even with selected key combination from the preferences.
Also, xorg uses up a lot of CPU (25-50%), when just listening to music with audacious and writing this thread, this is unusual compared to the old version.

In rest it works just perfect.

So  if anyone knows how to check out this video card problem, please tell me, I don't want to go back to the old 7.10 version.

Thanx guys

---

### Post by duruttye on 2008-10-14
Bump:(

---

### Post by dabl on 2008-10-14
> **duruttye said:**
> 
  if anyone knows how to check out this video card problem, please tell me



In the console:

```
lspci
``` will show the name of the video controller

Once you know that, you can decide (after searching this forum, perhaps) whether a suitable proprietary driver exists, and if so, how to install it.

  ;-)

---

