---
title: "black screen"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by rog64 on 2013-02-24
hi, i helped my friend install ubuntu 12.04 from a cd..everything worked fine that day but when he turned on the laptop the next day, the screen was black, but everything seems fine when hooked up to another monitor..even when we tried to boot windows 7, the screen was still black..any ideas

---

### Post by MAFoElffen on 2013-02-24
> **rog64 said:**
> hi, i helped my friend install ubuntu 12.04 from a cd..everything worked fine that day but when he turned on the laptop the next day, the screen was black, but everything seems fine when hooked up to another monitor..even when we tried to boot windows 7, the screen was still black..any ideas

Since it is a laptop... the first thing to do would be to (while is is running)... Hold a flashlight at an angle to the screen and see if it is totally blank --or-- if the screen is dsplaying but the backlight is just off.

Different avenues from there...

---

### Post by rog64 on 2013-02-24
hi, i used a flashlight and the screen was just blank..

---

### Post by MAFoElffen on 2013-02-24
> **rog64 said:**
> hi, i used a flashlight and the screen was just blank..

Then what make and model laptop(?) so I can get an idea of the spec's and what kind of video it has.

---

### Post by UltimateCat on 2013-02-24
> **rog64 said:**
> hi, i helped my friend install ubuntu 12.04 from a cd..everything worked fine that day but when he turned on the laptop the next day, the screen was black, but everything seems fine when hooked up to another monitor..even when we tried to boot windows 7, the screen was still black..any ideas
You could try booting to a LIVE DVD/CD.
If the machine boots see if you can see and mount the hard drive-
If not it is possible that the screen/monitor might have be undrgoing hardware failure.


This solved thread should help:

SOLVED Black Screen:
[http://ubuntuforums.org/showthread.php?t=1966128](http://ubuntuforums.org/showthread.php?t=1966128)

---

### Post by MAFoElffen on 2013-02-24
> **UltimateCat said:**
> You could try booting to a LIVE DVD/CD.
If the machine boots see if you can see and mount the hard drive-
If not it is possible that the screen/monitor might have be undrgoing hardware failure.


This solved thread should help:

SOLVED Black Screen:
[http://ubuntuforums.org/showthread.php?t=1966128](http://ubuntuforums.org/showthread.php?t=1966128)
UltimateCat-

Or if he goes half way down the 1st post of my Graphics Resolution Sticky in my sig line, there's a Linux Diagnostics Flow Chart... where you can step through Grub, kernel, Xserver, Desktop... to verify each is working or diagnose just where the problem is. It also directs what to do for each.

Most of the time after an install, on the first reboot, it is grub or the video driver... and with laptops in particular, lately there's been a lot of backlight issues.

You are right in that just saying if has a "black screen" could mean a whole lot of things, such as there is no power coming from the wall plug, through a bad video driver, with lots of things in-between. Have to rule out the obvious first.

To the OP-
You installed from a LiveCD... your first post said you installed from one. On a LiveCD, go to a terminal session and post the results of this:
```

lspci -vnn | grep -i VGA

```
Then reboot without the disk and as it gets past the BIOS Messages and the screen goes blank, press the left shift key.

See if the Grub menu comes up. If it comes up, grub is working. If not, then mount your installed sys from a LiveCD (2nd half of Post #3 of my Graphics sticky) and then reinstall grub. If you re-install grub and it still doesn't show with the hotkey, tell me and I will tell you how to force it to display.

If the Grub Menu appears, quickly press the down arrow once. Arrow back up one, then press "e". Go down to the first line that says linux and replace "quiet splash" with "Single --verbose". Then press <cntrl><x> to boot. 

If it stays blank, use the LiveCD mount intstructions to reinstall the kernel.

If it flashes kernel messages wizzing by, it's booting the kernel. If it hangs, noted were it says it stops. 

If it stops before or at the CPU probe, reinstall the kernel. It it hangs just after the CPU probe, reboot the PC and besides the before-mentioned bootline edits, also add "acpi=off".

If it boots to a text tty session, the kernel is good, and then I would/will continue with instructions from there...

---

