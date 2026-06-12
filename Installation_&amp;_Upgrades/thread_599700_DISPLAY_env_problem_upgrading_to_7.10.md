---
title: "DISPLAY env problem upgrading to 7.10"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Sparohok on 2007-11-01
I just upgraded from 7.04 to 7.10 and most stuff is working great. However I have a strange problem with my dual monitor layout. I have two X screens, :0.0 and :0.1. Previously, any graphical application started from screen :0.1 would show up on :0.1. Now, many times, programs I start on :0.1 show up on :0.0.

To be more specific:

1) When I start Terminal from the pulldown menu or from the top GNOME panel on screen :0.1, the terminal window shows up correctly on :0.1. However, the DISPLAY environment variable in that window is incorrectly set to :0.0. This is different from the behavior under 7.04, when the DISPLAY environment variable would always match the screen on which the terminal is running.

2) When I right click on an application icon in the top GNOME panel of screen :0.1, and select "Properties" from the drop down menu, the properties window always shows up on screen :0.0, which is incorrect behavior and different from 7.04.

I looked in /etc/profile and /etc/bash.bashrc but didn't find anything odd. Suggestions? Help?

Thanks,
Martin

---

### Post by Sparohok on 2007-11-02
Nobody?

---

