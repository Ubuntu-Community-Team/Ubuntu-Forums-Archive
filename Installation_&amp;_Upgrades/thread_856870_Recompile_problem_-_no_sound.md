---
title: "Recompile problem - no sound"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by Paul Lowman on 2008-07-11
OK - I have been at this for days on and off ...

I have made a small change to hid-quirks.c to enable the Logitech diNovo mini mouse pad and then recompiled the kernel using the recommended Ubuntu way with make-kpkg and the existing kernel config file (from /boot). Compiles fine and installed fine. Boots fine and the mouse pad even worked some where along the line - the problem is that the new kernel does not have any sound drivers loaded. I am completely stumped on this one. If I look at /lib/modules for the standard kernel (2.6.24-19-generic ) I see the following directories - initrd, kernel, madwifi, volatile plus some other files if I look at the directories for the new recompiled kernel most of these are not there including the ubuntu one which appears to have the sound drivers (amongst others).

My question is what am I missing? It seems that some other magic is required to duplicate the standard generic set up - I can find no reference to any other steps in this process.

Any help most appreciated ...

---

### Post by dk75 on 2008-07-12
Yes. You missing drivers.
Want ALSA - compile it.
Want madwifi - compile it.
Want anything else thats dependant on kernel version - compile it by hand.

That's the way of these who compiled it's own kernel - even these who didn't do any changes in it.
You could bear it or go back to "canonical" kernel.

---

