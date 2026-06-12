---
title: "Missing resolution options for ATI Radeon 9600"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by peppergrower on 2010-08-12
I just installed Ubuntu 10.04 on a friend's computer, and the graphics drivers don't seem to be quite correct.  The highest resolution available in Monitor Preferences is 1360x768; however, he has a 1920x1080 screen.  I know his graphics card (an ATI Radeon 9600 (RV350 AR)) is capable of the screen's native resolution, since it was working on Windows.  How can I enable this resolution?

I foolishly tried fglrx, but had to boot in recovery mode to remove it when the screen wouldn't display anything at all.  I did find this [page]("https://help.ubuntu.com/community/RadeonDriver"), and got as far as running `glxinfo | grep vendor`, but the output didn't match what the page seemed to expect.  (I got the following lines:

[INDENT]server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: DRI R300 Project[/INDENT]

Any help would be greatly appreciated!

Thanks,
peppergrower

---

