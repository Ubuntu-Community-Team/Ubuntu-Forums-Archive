---
title: "Screen flickering after logging in"
date: 2008-12-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by klim8 on 2008-12-31
Since few weeks ago the screen of my laptop flickers for 10-20 seconds when it is loading GNOME (cold start). I have an Intel 945GM chip and I am using the latest -intel driver from the Jaunty repositories. I have noticed that the following lines are printed many times in Xorg.0.log; and I think this can be related to the flickering problem:

(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0 71.00 1280 1328 1360 1440 800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "APP", prod id 40030
(II) intel(0): EDID vendor "APP", prod id 40030

Anyone else is having this problem?

I have opened a bug in launchpad: [https://bugs.launchpad.net/ubuntu/+bug/312518](https://bugs.launchpad.net/ubuntu/+bug/312518)

---

### Post by ShirishAg75 on 2008-12-31
klm8, 
 can you subscribe me to the bug. I am unable to resolve launchpad.net atm.

Update: subscribed to the bug. I would swing by Jaunty today and see if I get the same thing on my Xorg.0.log. I do have slight flickering on my desktop as well. On Intrepid atm.

---

