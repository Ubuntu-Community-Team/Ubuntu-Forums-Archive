---
title: "Xserver hangs on boot, screen rapidly flashing"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by sinnerman89 on 2012-03-28
Hi everybody; as you can understand from the title, i am struggling to get Xorg started.

I've  just finished repairing an old pc that was sitting around my room and i've tried to install Ubuntu on it. I booted from the live cd (which started  correctly, no errors or graphic bugs/glitches) and installed the OS on  my hard disk. But when i tried to boot from the hd, everything went  wrong: the screen began to flash (though to be precise i should say  flicker) rapidly, showing severe corruption of the image, and after a  while it freezes (while continuing to blink rapidly). I've tried to boot  to the command line, because i thought it was Xorg's fault, but  flickering happens right after grub has loaded the OS. 

But i've managed to solve the problem: after rebooting various times, it "correctly" loaded the Xserver (though it was still flashing like hell, but at least i could work on it) and i compiled and installed the fglrx driver. Now everything is fine, but i still want to know what the hell happened, just for curiosity's sake.

Here's the pc running Ubuntu:
 
Pentium 4 3.2 Ghz, x86
Ram 2 GB
Asus HD 6450 SILENT (worst video card ever)

P.S: while troubleshooting, i've tried to run glxinfo from the livecd, because ithought that if the livecd boots fine, it is using the right driver; the result was:
Direct Rendering: yes
Driver: Gallium 0.4 on AMD CAICOS

---

