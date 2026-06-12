---
title: "Unity/Compiz complains opengl/glx"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by sinaen on 2013-02-06
After a year or so of abscense to ubuntu i decided i wanted to dump Windows 8 to Ubuntu 12.10 64-bit for apparent reasons

The installation went smooth as silk,
And happy unknowing that the problems was just beginning,

I Run a Acer Aspire TimelineX 4830TG 
With an NVIDIA Geforce 540M Graphics card

The first thing to do is to find appropriate drivers and programs
so i installed the package nvidia-* 
After upgrade and reboot, first time, the window-panels are missing in compiz/unity.[B]
I traced the problem to the graphics driver, it wont run nvidias, and it wont run opengl[/B]

Several solutions were found and tryed.
None of them worked, I acctually reconsiderd installing windows 7 again, but my fingers are more inclined for the terminal and console.
The current solution is to run xubuntu desktop where i get a working desktop environment.

The sollutions i found was to purge compiz, uninstall nvidia reinstall kernel modules etc etc... as i dont want to repeat myself you know the result.
Install NVIDIA drivers from their homepage. purged reinstalled, messed back and forth
as soon as i run nvidida-xconfig, the gdm displays a 640x480 display,

One package i couldt find nvidia-purge, for purging and reinstalling nvidia, it was broken

And i want my graphics driver to be correct so i can use HDMI and graphics acceleration.

The solutions i found are from the most of these links below:
[http://www.linlap.com/acer_aspire_4830tg_timelinex?&#comment_47ba8b61c69cedaedfbea3b63442ebcc](http://www.linlap.com/acer_aspire_4830tg_timelinex?&#comment_47ba8b61c69cedaedfbea3b63442ebcc)
[http://ubuntuforums.org/showthread.php?t=1676476](http://ubuntuforums.org/showthread.php?t=1676476)
[http://askubuntu.com/questions/204778/unity-completely-broken-after-upgrade-to-12-10](http://askubuntu.com/questions/204778/unity-completely-broken-after-upgrade-to-12-10)
[http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/)
[http://wiki.compiz.org/Hardware/NVIDIA](http://wiki.compiz.org/Hardware/NVIDIA)
[http://ubuntuforums.org/showthread.php?t=1959496](http://ubuntuforums.org/showthread.php?t=1959496)
[http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers)
[http://forums.freebsd.org/showthread.php?t=31586](http://forums.freebsd.org/showthread.php?t=31586)

some drawouts from xorg.log 

[    11.447] (II) LoadModule: "glx"
[    11.450] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    11.452] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    11.452]    compiled for 6.9.0, module version = 1.0.0
[    11.452] (II) Loading extension GLX

[    11.457] (II) LoadModule: "nvidia"
[    11.458] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    11.464] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.464]    compiled for 4.0.2, module version = 1.0.0
[    11.464]    Module class: X.Org Video Driver
[    11.513] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    11.513] (EE) NVIDIA:     system's kernel log for additional error messages.
[    11.513] (II) UnloadModule: "nvidia"
[    11.513] (II) Unloading nvidia
[    11.513] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    11.513] (==) Matched intel as autoconfigured driver 0
[    11.513] (==) Matched vesa as autoconfigured driver 1
[    11.513] (==) Matched fbdev as autoconfigured driver 2

My xorg.config file (the best parts):
Section "Module"
    Load           "glx"
EndSection

Section "Device"
    Identifier     "Device"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Device"
    SubSection     "Display"
        Modes      "nvidia-auto-select"
    EndSubSection

As i can see from the log, it seems not to be able to load the NVIDIA modules.

---

