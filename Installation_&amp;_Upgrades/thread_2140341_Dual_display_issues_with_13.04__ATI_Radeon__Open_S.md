---
title: "Dual display issues with 13.04 / ATI Radeon / Open Source"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by jdholman on 2013-04-29
I did a fresh install of 13.04 on my Dell Precision M6500.  I was previously running 12.04 LTS.  My laptop has an ATI Mobility Radeon HD 5870 adapter and I'm using the open source driver.

Plugging in an external display on boot enables mirroring which is nice by default.  Since I want to run this off to extend my display, I use the display adapter utility to uncheck mirror and apply.  about 50% of the time, I get a crash of Unity and/or Compiz. 

I lose the launcher and the title bars on my window and the ability to change windows.  Pretty scary stuff since 12.04 LTD didn't have this problem.  To recover my apps, I do a Ctrl-Alt-F1 to get to a terminal, log in, cross my fingers, and run:
unity --replace
or
DISPLAY=:0 unity --replace

I then do a Ctrl-Alt-F7 and pray that my apps respond again so that I can close them and restart.  If I don't get my apps to respond, I'll try this from a console terminal:
DISPLAY=:0 compiz --replace

This will sometimes get my apps back, albeit without Unity.  At least I can close them gently.  If I can't get my apps back, I have to close the apps I can and restart via Ctrl-Alt-Del and home that my hidden applications panic.

I will also get Unity / Compiz crashes when using Shutter and sometimes when accessing the Stormcloud weather application.

I tried the proprietary ATI drivers, and they were worse, with Mirroring on by default and attempting to unmirror via the ATI utility or the Ubuntu display manager not working either.  I was also getting the virtual display adapter resolution error and I wasn't ready to have manually maintained a xorg.conf file.

Here are some display particulars for my system:
jim@jim-Precision-M6500:~$ lspci -nnk | grep -i vga -A3
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Broadway XT [Mobility Radeon HD 5870] [1002:68a0]
    Subsystem: Dell FirePro M7820 [1028:12ef]
    Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Juniper HDMI Audio [Radeon HD 5700 Series] [1002:aa58]
jim@jim-Precision-M6500:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD JUNIPER
OpenGL version string:  3.0 Mesa 9.1.1


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes


So I'm quite frustrated at this point and the 3 to 5 Unity crashes a day are unproductive.

Any advice out there?

Thanks,

Jim

---

