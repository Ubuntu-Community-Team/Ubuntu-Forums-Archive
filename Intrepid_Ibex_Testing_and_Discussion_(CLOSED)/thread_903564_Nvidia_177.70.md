---
title: "Nvidia 177.70"
date: 2008-08-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-08-28
[http://www.nvnews.net/vbulletin/showthread.php?t=118602](http://www.nvnews.net/vbulletin/showthread.php?t=118602)

---

### Post by pureblood on 2008-09-14
I just installed the nvidia-glx-177 intrepid package on my kubuntu hardy machine and the Desktop improvements are huge (I use KDE4.1 with a GeForce 6200). I think the package should be a suggested update for everybody running kubuntu hardy. Although, it was necessary to reboot the machine to avoid nvidia module conflicts.

---

### Post by jlacroix on 2008-09-14
I'll be happy when Nvidia fixes all the KDE 4.1 inconsistencies.

---

### Post by doorknob60 on 2008-09-14
> **jlacroix said:**
> i'll be happy when nvidia fixes all the kde 4.1 inconsistencies.

+1

---

### Post by Crinos512 on 2008-09-15
> **jlacroix said:**
> I'll be happy when Nvidia fixes all the KDE 4.1 inconsistencies.

+ another 1 :)

---

### Post by MaX on 2008-09-15
I'll be happy when I can use the latest kernel and still have my nvidia setup...

---

### Post by jlacroix on 2008-09-15
Is 177.70 final, or is it still beta? I remember them saying that this would fix the Nvidia issues but that hasn't happened yet, which is why I'm thinking it's still beta.

---

### Post by Nullack on 2008-09-16
nvidia.com has the answer for you ;)

beta

---

### Post by Chareos on 2008-09-16
> **pureblood said:**
> I just installed the nvidia-glx-177 intrepid package on my kubuntu hardy machine and the Desktop improvements are huge (I use KDE4.1 with a GeForce 6200). I think the package should be a suggested update for everybody running kubuntu hardy. Although, it was necessary to reboot the machine to avoid nvidia module conflicts.

How did you did this ?
Just got the package and installed via dpkg ?
Is is compatible with the latest Hardy kernel (backports/proposed enabled) ?

Thank you for any hint

---

### Post by plun on 2008-09-20
177.76...



New beta version out

[http://www.nvnews.net/vbulletin/showthread.php?t=119682](http://www.nvnews.net/vbulletin/showthread.php?t=119682)

    * Added support for the following new GPUs:
          o GeForce 9500 GT
    * Fixed a bug that caused GPU errors when applications used the X RENDER extension's repeating modes in conjunction with color-index overlays or rotation on GeForce 7 series and older GPUs.
    * Fixed a bug that caused system hangs when using the NV-CONTROL interface to change GPU clock frequencies.
    * Fixed a text rendering performance regression on GeForce 7 series and older GPUs when InitialPixmapPlacement is set to 2.
    * Updated mode validation, in cases when no EDID is detected, such that 1024x768 @ 60Hz and 800x600 @ 60Hz are allowed, rather than just 640x480 @ 60Hz.
    * Improved power management support.
    * Improved compatibility with recent Linux 2.6 kernels.
    * Fixed a regression that caused the 'Auto' SLI X option setting to not enable SLI.
    * Added a workaround for broken EDIDs provided by some Acer AL1512 monitors.


And a packaging request...:)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/272572](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/272572)

---

### Post by pferraro on 2008-09-20
FYI - 177.76 has some unfortunate 2D performance regressions:
[http://www.nvnews.net/vbulletin/showthread.php?t=119719](http://www.nvnews.net/vbulletin/showthread.php?t=119719)
Maybe we'll see a 177.77 in the next couple days like with .67/68...

---

### Post by phenest on 2008-09-20
Despite the 2D performance problems, at least this one hasn't crashed on me like the other 177.x's. At least, no yet...

---

### Post by phenest on 2008-09-21
Spoke too soon. This driver also crashes on me.

---

### Post by phenest on 2008-09-22
> **plun said:**
> And a packaging request...:)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/272572](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/272572)

Well, they've packaged it. Got it amongst the many updates I got today. Shame it doesn't work for me.

---

### Post by Nullack on 2008-09-22
Have you tried some debugging? Have a look for tips on the ubuntu wiki.

---

### Post by plun on 2008-09-22
Maybe its better to go directly to nVidia ?

[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

A little tricky to kill gdm from tty and then start a new X session
in log mode.


Kernel 2.6.27-4 is also soon available...

---

### Post by phenest on 2008-09-22
> **plun said:**
> A little tricky to kill gdm from tty and then start a new X session
in log mode.

That's the problem. All I can do is switch to tty and Ctrl-Alt-Delete. I will look into debugging.

---

### Post by phenest on 2008-09-22
I can't seem to install nvidia-glx-177. Some file conflicts with package xserver-xorg-core.

However, I installed the 177.76 driver from nVidia. I have also set CPU speed to performance according to [bug 109643]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643"). Let see if that fixes my problem.

---

### Post by Sef on 2008-09-22
> I can't seem to install nvidia-glx-177.

Same here.  Here is my [thread]("http://ubuntuforums.org/showthread.php?t=927216") if anyone has an answer.

---

### Post by plun on 2008-09-27
[B]nVidia 177.78
[/B]
    *  Fixed a performance regression affecting the gtkperf lines and circles test.
    * Updated the X driver to consider /sys/class/power_supply when determining the AC power state.
    * Fixed corruption when using SLI in SFR mode with OpenGL-based composite managers.


[http://www.nvnews.net/vbulletin/showthread.php?t=120052](http://www.nvnews.net/vbulletin/showthread.php?t=120052)


Manual:
[ftp://download.nvidia.com/XFree86/Linux-x86/177.78/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/177.78/README/index.html)

File a update request.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/275098](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/275098)

---

### Post by phenest on 2008-09-27
> **phenest said:**
> I have also set CPU speed to performance according to [bug 109643]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643"). Let see if that fixes my problem.

No it didn't.

177.78, eh? Let's try that then.

---

