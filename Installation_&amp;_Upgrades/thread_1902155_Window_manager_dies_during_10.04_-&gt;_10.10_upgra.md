---
title: "Window manager dies during 10.04 -&gt; 10.10 upgrade"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by Jeff Abrahamson on 2011-12-30
During the 10.04 LTS -> 10.10 upgrade, I find myself with the update grub dialog.  Unfortunately, it's action buttons are *behind* the upgrade progress dialog, and I have lost window decorations (so can't change window stacking order).  This seems to indicate that the window manager has died, because I can use the mouse but not the keyboard.

So the upgrade appears to be dead in the water for inability to tell the grub upgrade to go ahead.  I can launch a terminal, but I can't type to it. :(

Any suggestions besides reboot?

On reboot, any suggestions for what to do next?  (In the absence of response, in a few hours I'll reboot and look at how to recover, updating this thread.)

Thanks for any tips.

---

### Post by Jeff Abrahamson on 2011-12-30
I've filed this bug report, which describes the problem and its resolution.

    [https://bugs.launchpad.net/bugs/910051](https://bugs.launchpad.net/bugs/910051)

Briefly, the resolution was an hour or so of clicking and poking and typing to no effect, until mysteriously the upgrade understood a respond and started again.  Unsatisfying as a response but ok as an outcome.

---

