---
title: "partitions error when trying to install 9.10"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by Affrikka on 2009-11-21
Hey everyone,

I have tried to install 9.10, and when i get to the "select a partition" screen, there doesn't appear to be ANY paritions at all on the chart. It won't let me click any buttons on the screen either, except revert, which just changes the mouse into that loading circle thingy and it sits there (i left it sit like that all school day and it was "still loading")
Is there anything I can do to make it see that i actually have a hard drive, and it needs to use it?


thanks!


Mathieu

---

### Post by Affrikka on 2009-11-25
bump.... sorry I really would love to install 9.10 since 9.04 isn't working either, same error..same with 8.04.... and I'd really like to get it installed so I can set up a virtual box with windows 7 in it and do my A+ homework :P haha

---

### Post by dhavalbbhatt on 2009-11-25
I would recommend a couple of things -

If you are using the desktop installation CD, then boot in LiveCD environment. From here on, open Synaptic and do a search for dmraid. Remove the first two packages that show up (these should be installed packages). Once you have done that, you can reboot with the CD in the drive and install it.

The other thing that I would suggest you do is, burn an alternate installation CD - it does not have a GUI, is CLI based, but does the job just fine.

Bottom line is, partition manager in desktop installation seems to be broken and removing dmraid seems to resolve any issues.

---

### Post by Affrikka on 2009-11-25
thank you so much!!! it works now! yay! i'm currently installing it now :) thank you again so very much!

---

