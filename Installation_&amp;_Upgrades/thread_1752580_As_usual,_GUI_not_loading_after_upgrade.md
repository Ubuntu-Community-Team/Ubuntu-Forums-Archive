---
title: "As usual, GUI not loading after upgrade"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by Dave M G on 2011-05-08
Sorry, but I need to rant a little here.

Literally every single time I upgrade Ubuntu, going back more versions than I can remember, I have had problems with the Nvidia drivers, or Xorg, or something. Each time it's a little different, and each time I have to spend hours trying to figure out how to simply get Ubuntu to display.

Will there ever be a time when I can take a perfectly working version of Ubuntu and upgrade it without it breaking?

Okay, rant over. Needed to get that out of my system.

Now, here's the current problem.

I boot, and Ubuntu gets to the purple splash screen, where the orange/white dots indicate progress.

Then, eventually the dots remain all white (or all orange), and that's where it stops.

I can log in by SSH, I can boot into a command prompt... it seems to be installed and operational, except I have no graphics.

I have tried purging and reconfiguring xserver-xorg, I have tried deleting /etc/X11/xorg.conf, I have tried reinstalling the Nvidia drivers. All solutions that have worked in the past.

This time, no go. Like I mentioned above, each time the problem is a little different.

For some reason, it seems to be loading a "vesa"(?) module, and saying I don't have the drivers available.

This is the output of Xorg.failsafe.log:

```
[    53.789] (II) LoadModule: "vesa"
[    53.789] (WW) Warning, couldn't open module vesa
[    53.789] (II) UnloadModule: "vesa"
[    53.789] (II) Unloading vesa
[    53.789] (EE) Failed to load module "vesa" (module does not exist, 0)
[    53.797] (EE) No drivers available.
[    53.805] 
Fatal server error:
[    53.821] no screens found
```

So what do I need to do this time just to get X up and running?

Any advice would be much appreciated.

Thank you for your time.

---

### Post by MAFoElffen on 2011-05-08
> **Dave M G said:**
> Sorry, but I need to rant a little here.

Literally every single time I upgrade Ubuntu, going back more versions than I can remember, I have had problems with the Nvidia drivers, or Xorg, or something. Each time it's a little different, and each time I have to spend hours trying to figure out how to simply get Ubuntu to display.

Will there ever be a time when I can take a perfectly working version of Ubuntu and upgrade it without it breaking?

Okay, rant over. Needed to get that out of my system.

Now, here's the current problem.

I boot, and Ubuntu gets to the purple splash screen, where the orange/white dots indicate progress.

Then, eventually the dots remain all white (or all orange), and that's where it stops.

I can log in by SSH, I can boot into a command prompt... it seems to be installed and operational, except I have no graphics.

I have tried purging and reconfiguring xserver-xorg, I have tried deleting /etc/X11/xorg.conf, I have tried reinstalling the Nvidia drivers. All solutions that have worked in the past.

This time, no go. Like I mentioned above, each time the problem is a little different.

For some reason, it seems to be loading a "vesa"(?) module, and saying I don't have the drivers available.

This is the output of Xorg.failsafe.log:

```
[    53.789] (II) LoadModule: "vesa"
[    53.789] (WW) Warning, couldn't open module vesa
[    53.789] (II) UnloadModule: "vesa"
[    53.789] (II) Unloading vesa
[    53.789] (EE) Failed to load module "vesa" (module does not exist, 0)
[    53.797] (EE) No drivers available.
[    53.805] 
Fatal server error:
[    53.821] no screens found
```So what do I need to do this time just to get X up and running?

Any advice would be much appreciated.

Thank you for your time.
Have you  tried going through the troubleshooting flow chart in this sticky?
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Dave M G on 2011-05-08
> Have you tried going through the troubleshooting flow chart in this sticky?

Yes, in so far that I verified that my GRUB is loading and that I can select different kernels to boot.

Why would I need to configure GRUB to get my video to work properly? Doesn't GRUB just choose which OS to boot, and then the OS takes care of the graphics?

I think my head might explode if suddenly GRUB is now part of the equation after all these years of fighting Nvidia drivers.

---

### Post by Dave M G on 2011-05-09
Solution: Gave up on trying to fix it and instead did a fresh install.

---

