---
title: "Gusty upgrade broke video playback; graphics drivers upgrade broke refresh rates"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by jamespetts on 2007-12-09
I have just upgraded my mini-ITX system (VIA CX700M2) from Feisty to Gusty. Happily, the sound, which previously required compiling drivers from source, and refused to work if I booted with the updated kernel, now runs fine without any tinkering.

Unhappily, after I upgraded, I found that video playback was horribly corrupted. I thought that installing the Unichrome driver from the VIA Arena website (the one specifically for Gusty) would help. I thought that it might also be good to have a 3d driver to use desktop effects and use 3d applications such as SecondLife, but that wasn't critical. I installed it according to the instructions that came with it, but found that, after reboot, my CRT monitor was displaying only 60hz. Going into "screen resolution" gave me the option of 60 or 70hz, but the 70hz was currently selected, and the monitor was still at 60hz. Switching back and forward had no effect. I tried turning on desktop effects, and they failed to load, even after applying the fix recommended in the instructions, even though I could get the 3d test application "glxgears" to work fine. The video corruption problem was fixed.

I tried using xvidtune as recommended in the instructions also had no effect whatsoever on the refresh rate, despite purporting to set it to a different level (I can check the refresh rate on my monitor's menu). Previously, the monitor had been happily going at either 85Hz or 100Hz. I tried generating modelines to go into the xorg.conf, with no success. I then tried using the backed up xorg.conf from the previous configuration: when I did that, it refused even to boot into any GUI except using the failsafe VESA mode with 800x600 at 60hz (even though the video card drivers sections both gave the driver as "via").

I then tried restoring the previous xorg.conf that had been set by the initial configuration, albeit with my added modelines and added "vert refresh" and "horiz refresh" lines. Then, it would boot into the login screen (at 60Hz), but would then freeze, although the mouse cursor still responded, and CTRL+ALT+BACKSPACE worked.

I am now stuck at 60Hz with 800x600 and a VESA driver. Can anybody help? I have been trying for hours to make it work.

**Edit**: It is getting worse all on its own. When I restarted it, the screen flickered on and off a large number of times, I then get a message (not in any kind of GUI) saying, "The screen manager has shut down 6 times in the last 90 seconds. It is likely that something bad is going on". That is still there when I next reboot. I had not changed any settings since the time that I had last booted into the system and that I rebooted just before this occurred. I cannot now get into any sort of GUI at all. Can anybody help?

---

