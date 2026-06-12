---
title: "System Weirdness - Hard or Soft Problem?"
date: 2015-10-08
forum: Installation &amp; Upgrades
---

### Post by suprleg on 2015-10-08
I recently upgraded my kernel and hardware as documented here:[http://ubuntuforums.org/showthread.php?t=2296538](http://ubuntuforums.org/showthread.php?t=2296538)
New mobo, ram, and cpu.

Unfortunately I'm running into some strangeness. When I open a new browser window or terminal window the graphics and/or text loads in pieces and very slowly, drop down menus hang, things of that nature. If I run my cursor down a web page the text becomes visible or minimize a terminal and re-open it the text appears. 
The system doesn't feel laggy,but I'm encountering this odd behavior. I'm trying to decide if this is a kernel vs. hardware issue or perhaps a dying video card as the card, an old Nvidia gtx 550ti with the latest nvidia drivers 352.41, has been acting strangely. By strangely I'm referring to the fact that Folding at Home just hangs while attempting to use the GPU slot and the card runs hotter than normal at idle, 40C-60C. I've tried setting the bios the "Auto" and "gen2" for the GPU, but don't notice any appreciable difference.
Ideas?

---

### Post by suprleg on 2015-10-09
I'm going to bump this thread, surely after 100+ views someone must have an opinion whether this is a hardware or software issue..?

---

### Post by tgalati4 on 2015-10-09
Old video cards need maintenance.  Have you blown out the dust in the GPU fan?  Have you replaced the heat sink grease on the GPU?  It's possible that when the GPU gets hot, it throttles back the speed to save itself.  Once you have gone through the hardware, then you are in a better position to assess its performance.

Only after cleaning, run *glxgears* and report your framerate.  Mixing an old graphics card with a new motherboard and CPU can cause integration issues (bus timing, bad interrupts, etc) which are difficult to troubleshoot in a forum.

---

### Post by ubfan1 on 2015-10-09
I'd also doublecheck what video driver you are actually running.  try lsmod |sort  and see if you get nvidia as expected, or nouveau, the (unexpected) default, or even just VGA (some fallback).  Other ways to check would be lspci -v   and see what driver is in use for the video.  lshw -C video  will also tell you.  With both intel and Nvidia video present, you might even be running the i915 video.  Sounds like a hybrid system, so see what the bumblebee package has to offer.

---

### Post by suprleg on 2015-10-09
Thanks for the replies, yes the GPU was completely cleaned and new TMI applied before reinstalling  into the new motherboard. I also manually updated  to *Nvidia drivers: 352.41. This:"*Mixing an old graphics card with a new motherboard and CPU can cause integration issues (bus timing, bad interrupts, etc", was my initial though, just wanted to hear someone else's   opinion.

---

### Post by tgalati4 on 2015-10-09
If you have the old motherboard, put the video card in that and try to boot with a LiveUSB.  Give it a workout.

---

### Post by ubfan1 on 2015-10-10
Try using the Nvidia driver which last worked instead of 352.  I usually let the "nvidia-current" package select the proper driver for my hardware.

---

