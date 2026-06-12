---
title: "Sound problems after 7.10 to 8.04 Upgrade"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by Mad-Halfling on 2008-05-02
I've upgraded from 7.10 to 8.04 and it all seemed to go through OK, but the sound is now shot - it still "works" and plays music files but the sound is really crackly and is nothing like it was under 7.10 where it was nice and clean.

I've got an HP Paillion 6000ae and device manager reports the sound as an intel 82801G (ICH7 Family) High Definition Audio Controller - anyone else having this issue with sound deterioration?

---

### Post by Mad-Halfling on 2008-05-02
Seemed to have solved this, not sure why, but here's something to try.
Right-click the volume icon and select [Open Volume Control] then reduce the level of the PCM volume, play a bit of music, this ma have fixed the quality problem, you can then put the PCM back to it's original value (mine was at max) and the quality will still be ok - I'm guessing there is an initial calibration problem with the volume control that's causing the PCM to be way off the scale to start with, but changing it resets it and corrects the problem

---

### Post by kcramakrishna on 2008-09-09
Yes, that worked for me - Thanks a **_lot_**. I upgraded from Ubuntu 7.04 to 8.04 on a Compaq V6120US with Nvidia GeForce Go 6150.

The screen resolution was broken too and here is how I fixed it:
[LIST=1]
[*]I had the nvidia-glx driver already installed.
[*]I downloaded and installed the nvidia binary driver from nvidia web-site.
[INDENT][INDENT][LIST=1]
[*]I did a "Ctrl + Alt + F1".
[*]Then typed "/etc/init.d/gdm stop", Enter
[*]I installed the driver - it asked to compile some kernel headers which I allowed.
[*]root@kc-laptop:~# bash /root/NVIDIA-Linux-x86-173.14.12-pkg1.run
[/LIST][/INDENT][/INDENT][*]I rebooted the machine. Graphics came up fine.
[*]I went to /etc/X11/xorg.conf and changed the driver from "nvidia" to "nv"
[INDENT][INDENT]
   Section "Device"
    Identifier     "Device0"
   [COLOR="Red"] Driver         "**nv**"[/COLOR]
    VendorName     "NVIDIA Corporation"
   EndSection[/INDENT][/INDENT]
[*]I rebooted the machine and graphics are fine with the built in Ubuntu drivers.
[INDENT][INDENT][LIST=1]
[*]I again did a "Ctrl + Alt + F1".
[*]Then typed "/etc/init.d/gdm stop", Enter
[*]I un-installed the nvidia binary driver -
[*]root@kc-laptop:~# bash /root/NVIDIA-Linux-x86-173.14.12-pkg1.run --uninstall
[/LIST][/INDENT][/INDENT][*] Rebooted the machine to get full graphics.
[/LIST]

---

