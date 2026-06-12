---
title: "Can't connect to wireless"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by anna_sh on 2011-05-03
Hey,

I just upgraded my Ubuntu to 11.04 and now my wireless does not work, nor can I see the available networks. I use Dell inspiron N4010 64-bit with dual bootup with Windows 7. 

Any way to fix this issue? :confused:

---

### Post by MurphysLaww on 2011-05-03
You may have the dreaded broadcom chipset based b4311 wireless card. If you do,

see this thread:

[http://ubuntuforums.org/showthread.php?p=10761208#post10761208](http://ubuntuforums.org/showthread.php?p=10761208#post10761208)

or my own:

[http://ubuntuforums.org/showthread.php?t=1747694](http://ubuntuforums.org/showthread.php?t=1747694)

I'm still trying to solve this so that It will run when at startup but for now, I can get wireless up by going into a terminal window and typing this:

sudo modprobe --ignore-install b43

from my admittedly limited experience, and from reading some things from the Broadcom notes on this device here:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

it seems that several modules are loading that shouldn't be even though they have been blacklisted, such as b43, and/or ssb

This is causing a conflict with the STA driver which is what should be loading.

Hope this helps. I am on a dell as well

---

