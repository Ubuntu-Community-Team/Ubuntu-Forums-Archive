---
title: "update manager able to hide/ignore specific update?"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by NicoleM on 2007-04-18
(i posted this in the newbie forum the other day but never got any responses even after a few bumps.  This forum might be a more appropriate place anyway...i apologize for the cross post)


i recently installed proprietary ATI drivers using the envy program and all seems to have worked well. I now have the following listed as an update in my update manager:

fglrx-kernel-source
ATI binary kernel module source
from version 8.28.8-1 to 8.28.8+2.6.17.7-11.2 (Size: 685KB)

under the description it says

This package builds the ATI XFree86 4.x/X.Org binary kernel module needed by xorg-driver-fglrx.
**This package is not needed on an Ubuntu system because a pre-compiled kernel module is supplied by the linux-restricted-modules packages.**

great...i don't need it. aside from unchecking it each time i look at updates, is there a way to make the update manager ignore this particular update?

The reason it bothers me is because when i do a sudo apt-get upgrade it always shows up and I like being able to upgrade everything that needs to be upgraded in one shot as opposed to doing the apt-get command for each program that needs to be upgraded.

basically, my ATI drivers seem to be working fine, and I'm worried I'll accidentally install this and mess something up so is there a way to tell the update manager to disregard this update or if that's not possible does anyone know if going ahead and installing this update will break something?

---

### Post by NicoleM on 2007-04-18
bumpppppp

---

### Post by NicoleM on 2007-04-19
last shot at bumping

i plan on installing feisty but i have a feeling this issue will still be relevant so i appreciate any help i could get! :)

---

### Post by Angry penguin on 2007-04-19
i dont think there is a way to do that, i wanted to ignore a package once and i ended up disabling the update manager just to get it to shut up. 

But, it has been a little while since i looked into it last...

EDIT: Just found this:
[http://ubuntuforums.org/showthread.php?t=227088&highlight=disable+update+manager](http://ubuntuforums.org/showthread.php?t=227088&highlight=disable+update+manager)

---

### Post by NicoleM on 2007-04-19
thank you!  that was exactly what i needed.

i really appreciate your response...i feel a little silly that i couldn't find that thread myself though.

thanks!

---

