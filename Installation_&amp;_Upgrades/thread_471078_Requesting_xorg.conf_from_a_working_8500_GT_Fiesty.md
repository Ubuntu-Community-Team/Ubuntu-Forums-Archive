---
title: "Requesting xorg.conf from a working 8500 GT Fiesty install."
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by ericdsr on 2007-06-11
Unfortunately, getting the driver to work on my nvidia 8500 GT-based video card is turning into quite a chore. Envy won't even do the job. For some reason. xorg.conf is not getting set up right for the new card. Looking at a working xorg file might point me in the right direction. Thanks...

---

### Post by ajeannotte on 2007-11-13
i just installed fiesty fresh on a system with a nvidia 8500 as well. huge problems. i've tried everything i know but envy, nothing worked. i'm pretty new though, so i probably didn't try everything but no luck so far. 

a problem for another day for me though, it's time for sleep.


EDIT: ok, i got it working on 7.10, and i assume the same steps will work for 7.04. I used the synaptic package manager, made sure to enable all repositories from the menu, and searched for nvidia-glx-new.
after installing that, open a terminal and type: sudo nvidia-glx-config enable
reboot, or logout and do a CNTL+ALT+BACKSPACE or CNTL+SHIFT+BACKSPACE, whichever one restarts xserver. 

done.

EDIT: THE CORRECT WAY TO DO THIS is to go to the administration menu and select 'RESTRICTED DRIVERS'. If you're using a video card it should show up telling you you're not using the restricted driver that is designed for your hardware. Check the box saying you want to use the restricted driver. It will ask you to restart.... so restart. Done. After the reboot you'll have a message telling you that the restricted driver is in use. This is a one-time message, nothing to worry about.

---

