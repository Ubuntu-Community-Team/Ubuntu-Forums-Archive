---
title: "x server won't start"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by oldmanstan on 2007-04-20
i noticed other people were having this problem but they all seemed to have ati cards, i have an nvidia 6800 so i thought a new post might be in order

i used sudo apt-get dist_upgrade for the upgrade (the ubuntu site wasn't working last night so i didn't get a chance to see the instructions telling me to do otherwise, i was just too excited...)

anyway, a couple things: first, my "main" hard drive (hda) is actually not the one i use, this stems from the fact that i used to dual boot windows and since it went linux-only hda now has random distros that i happen to be trying (opensuse at the moment which is what i'm using now)

as a result grub gets confused sometimes, the menu.lst file still shows to old kernel, 17-11, is that a problem? i changed it to 20-15 but ubuntu hung when booting after that

ok, second, i had previously installed beryl from quinn's repos and the proper packages may not have been downgraded as apparently they needed to be.  i have since commented out those repos and attempted to fix the problem but i'm not sure if it worked.

ok, here is the grepped output from my xorg log file, i pulled out all the errors, then all the warnings:

errors
```
(EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
(EE) Screen(s) found, but none have a usable configuration.
```

warnings
```
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
(WW) open /dev/fb0: No such device
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
```

anyone have any ideas?  i've been banging on this for hours, can't think of anything else to try, i got rid of the nvidia driver and went back to nv (usually that solves problems to at least get me X) but no dice.

any help would be peachy!

---

### Post by jamespi on 2008-02-15
hi,

i'm running feisty and i have the same problem - did anyone ever figure this out? the vesa drivers are horrifically slow so i need to get nv working ASAP. 

thanks,
james

---

