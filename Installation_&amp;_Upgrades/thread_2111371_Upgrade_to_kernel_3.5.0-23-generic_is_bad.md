---
title: "Upgrade to kernel 3.5.0-23-generic is bad"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by UnixDon on 2013-02-01
I have been running 12.10 kernel 3.5.0-22-generic for some time now with no problems.  This morning I noticed that there were new updates to install so I installed them.  One of the updates was a new kernel version: 3.5.0-23-generic.  When I rebooted after that upgrade and logged in my screen consisted only of the main window with the icons that are on it.  There is no launcher and no menu bar at the top.  The HUD also does not work.  When I managed to bring up a window (by right clicking on the background), the window had no decorations (i.e. no close, minimize, maximize buttons, etc.).  None of the alt-F1, etc. keys work either.

My grub does not present me with a list of kernel versions like it used to prior to my latest install on this machine so I could not boot into an older kernel. 

I finally managed to get a text window up during reboot and put all of the new files in /boot (the ones with the *-23-* in them) into a scratch directory and rebooted.  After a few complaints from grub about not being able to find the 3.5.0-23 files, it finally gave me a choice to boot back into 3.5.0-22 which I did.  Everything is back to normal now.

It looks like this new kernel has a serious issue!

BTW, how can I enable the grub menu that normally comes up?  At least that makes it easier to recover from things like this.

---

### Post by arpanaut on 2013-02-01
I can't remember exactly but the NEW Grub 2 offers under the current kernel and recovery an option Additional or Other selection and after selecting that the previous kernel option are there.

If you have installed video drivers from the OEM you will need to reinstall them after each kernel upgrade. (I'm not positive on this and there may be other things like the kernel headers that need to be installed also) Hopefully those in the know will respond.

---

