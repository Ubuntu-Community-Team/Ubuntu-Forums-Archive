---
title: "Screen resolution with 14.10 Live CD doesn't let me see or push buttons to install"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by Voluntaryist on 2015-01-06
I just got a new computer running dual GeForce 970 cards in SLI with a 28" 4K monitor. I am trying to install Kubuntu 14.10. At the beginning of the installation, the window that asks if you want to try it or install it is so big, and the resolution is so large, that I cannot see or push the proper button to begin installation. I've tried every kind of window moving and resizing to see the buttons, to no avail. 

Any ideas as to how I can get this window small enough to see the install buttons?

---

### Post by mastablasta on 2015-01-06
take one of the cards out? 

or a workaround use minimal install iso or one button installer or something similar. install in pure text mode, install drivers manually, then finally install Kubuntu desktop &reboot.

another silly option - use buttons on monitor to move around a bit.

---

### Post by Voluntaryist on 2015-01-07
Thank you, those sound like a good ideas. I am going to try adjusting the monitor first, and if that doesn't work I'll try using a smaller, older monitor that will hopefully default to a different resolution. If that doesn't work, I'll try removing the video cards and using the motherboard's integrated video. Let's hope it works!

---

### Post by MAFoElffen on 2015-01-07
I've been an NVidia owner since 2005. Since early SLI, I've installed with one card present, until after the nvidia driver is installed, then physically re-inserted the other cards.

Think of it this way. Basic graphics tries to probe multiple cards that are exactly the same (as it see's it) and provides a single driver (that does not know how to distinguish between multiple cards that are the same), so when the basic driver loads, it ends in a conflict, trying to drive both cards as the same.

I don't know that the opensource drivers have SLI logic, because SLI is proprietary... So since then I just assumed, that was the way to do it. I've never a problem with that since, doing it that way. Sounds like the logic has changed "some" since... because what used to happen with that was that both screens would be dead...

What I do for res, is boot the LiveCD and use a kernel boot option to set the startup res.

---

### Post by Voluntaryist on 2015-01-08
Going with the single video card solved my install problem. I now have it up and running, thank you everyobdy! :)

---

### Post by MAFoElffen on 2015-01-10
Glad I could help.

Since resolved, please revisit this thread. Use the "Thread Tools" link in the upper left of the page and "Mark As Solved"

---

