---
title: "screen goes blank  on boot"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by karatekid on 2008-07-04
i have been trying to run ubuntu 7.10 from the cd , but no success till now.
everytime the cd boots the screen goes blank  after some time and i have no option but to reboot.
i then removed the quiet and splash parameters from the  command line and now iam able to somehow get to the command line terminal but could not figure out what to do next.
also sometimes i get the message 
x-server has shutdom 6 times in the past 90 seconds, so wait 2 minutes.
before this i had tried to install ubuntu 5.10 and ended with the same problem. But then i booted with the "live expert" mode and selected the vesa driver in display driver and then finally managed to get to the desktop.(however i even then could not use ubuntu because that cd had some errors, but the fact was that i could atleast get to the desktop).

i am using 
intel Pentium 4 3.0 Ghz with HT technology
intel desktop board D101GGC
ATI Raedon Xpress 200 series
512 Mb Ram (Kingston)
80 GB SATA hard disk (Hitachi)

note: i have never used linux earlier and hence don't know how to use the command line interface.

---

### Post by karatekid on 2008-07-04
i think i came across a solution .

"People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf."

could anyone tell me how to implement it??

---

