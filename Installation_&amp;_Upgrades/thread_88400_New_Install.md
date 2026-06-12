---
title: "New Install"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by Peter Scales on 2005-11-10
I am trying to install & have two problems

1,  when it completes the 1st stage & re-boots, 
     it seems to not intall Grub and/or LiLo
     After the reboot, I get either grub 1.5 loading error 17 or error 18
2,  if it gets past this into the 2nd stage, the last thing I see is
     starting GNOME    it then goes blank, as the vidio is switched off.

Any Ideas ??

:confused:

---

### Post by Manny C on 2005-11-10
You may have [not correctly setup your partitions]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors") during the installation process.

See [this Wiki entry]("https://wiki.ubuntu.com/Installation") for more help regarding partitioning. Under the *Basic Installation Methods* you should select your system type and read through the section detailing how to partition your disk.

---

### Post by Peter Scales on 2005-11-12
Okay that's point 1.
with No2.   it starts Gnome Display Manager,
then goes blank - looks like its switched off the vidio card ( S3 Trio)
The same occours with the Live CD.
I removed the higher levels of resolution it case it was the screen, but no...
IS there a low vga res I can try AKA mswin ??

---

### Post by maksenf on 2005-11-17
I had the same problem during the installation and my video card is the same: S3 Trio. I solved the problem by editing the /etc/X11/xorg.conf file in a command line session (press CTRL-ALT-F1). There was a line with something like DefautDepth set to 24 and my video card does not support that color depth. Once I set it to 16, the GDM came up and I was able to use resolutions up to 1024x768. I am still trying to set the resolution to a higher value (1280x1024 with color depth 8 or 1152x864 with color depth 16). Windows uses these higher resolutions, so obviously, the video card and the monitor support them.

---

### Post by Peter Scales on 2005-11-20
Cheers
I'll try that edit .. I was just about to give up !

I see that others are having Grub boot trouble too ..

---

### Post by maksenf on 2005-11-23
OK, A little follow-up. At the Color Depth = 16 I get the highest resolution 1024x768. At the Color Depth = 8 I get 1280x1024, 1152x864, as well as a number of other resolutions, however, the screen is somewhat grainy. I think the S3 Trio driver is not as good as the Windows driver. A little disappointed, but the grainy screen at 1280x1024 is better than clear screen at 1024x768.
Mike.

---

