---
title: "Nvidia 177.78"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-10-05
Has anyone heard from Alberto about .78?

---

### Post by autocrosser on 2008-10-05
narry a word as of yet--I could drop him a line to ask if you want....

---

### Post by ronacc on 2008-10-05
Alberto has been very good about getting us the latest and greatest , I'm sure it will appear soon .

---

### Post by autocrosser on 2008-10-05
I just sent a note his way--most likely will hear back in about 4~5 hours from now...bit late in Italy......

---

### Post by xebian on 2008-10-06
Just updated to the 27-5 kernel and am happy to let you know that 177.78 from NV is working very nicely.

---

### Post by plun on 2008-10-06
Alberto looks at this driver... beta freeze blocked it.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/275098](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/275098)

(and it works great but...... trashes RGBA scrolls again :) )


I hope we will have a final driver which also includes **[PhysX]("http://developer.nvidia.com/object/physx.html")**-support

---

### Post by Nullack on 2008-10-06
Plun Id settle for proper video acceleration myself :)

---

### Post by autocrosser on 2008-10-06
> **plun said:**
>  I hope we will have a final driver which also includes **[PhysX]("http://developer.nvidia.com/object/physx.html")**-support


Do I wish!!!!!!

---

### Post by autocrosser on 2008-10-06
I got my note back from Alberto--he is hoping for a week & a exemption from the freeze----here is wishing!!!!:)

---

### Post by ronacc on 2008-10-06
heck just put in his PPA and we'll handle the excepting:lolflag:

---

### Post by dabl on 2008-10-06
EnvyNG is the greatest!

But, while you're waiting ....

You can get the 177.78 driver from here:

[http://www.nvnews.net/vbulletin/showthread.php?t=120052](http://www.nvnews.net/vbulletin/showthread.php?t=120052)

Install the kernel-headers-$(uname -r) package, get out of X, and run the installer.  It works just fine here, on a 9600GT, on 2.6.27-5.  :)

---

### Post by Nullack on 2008-10-06
Nah, Ill wait for it in the repos to help testing ubuntu

---

### Post by autocrosser on 2008-10-06
I will also wait until Alberto gets it thru freeze....

---

### Post by ronacc on 2008-10-06
intrepid is the first version of Ubuntu where I haven't had to "roll my own" so I'm willing to give alberto a chance , but then with a 7600gs I have no serious issues with the current driver , if I had a problem card I would go for it .

---

### Post by plun on 2008-10-07
"Latest and the greatest"...:redface:


This one is important and it must be uninstalled otherwise a nVidia
driver from nVidia conflicts if a package driver is installed.(xorg files)

[ftp://download.nvidia.com/XFree86/Linux-x86/177.78/README/chapter-04-section-04.html](ftp://download.nvidia.com/XFree86/Linux-x86/177.78/README/chapter-04-section-04.html)


I hope for a final driver.....its still a beta driver.

---

### Post by xebian on 2008-10-07
The 27-5 kernel && 177.78 was a joy and it's making me want Kubuntu again.  The DE's were impressive, something I've never experienced before.

But today, got the 27-6 kernel and the 177.78 won't install.  :(

---

### Post by plun on 2008-10-07
> **xebian said:**
> 
But today, got the 27-6 kernel and the 177.78 won't install.  :(

This is how I sorted this out....

The failsafe options comes up  > choose to start in low graphics

Login screen comes up >  switch to the tty and stop gdm

Install driver > Restart gdm....  (edit or kdm...)


(I switched directly the first time and then I got a x-session which was impossible to kill and impossible to install a driver)

---

### Post by plun on 2008-10-07
News for "nVidia freaks"...   the driver is final  177.80

[http://www.nvidia.com/object/linux_display_ia32_177.80.html](http://www.nvidia.com/object/linux_display_ia32_177.80.html)

[http://www.nvidia.com/object/linux_display_amd64_177.80.html](http://www.nvidia.com/object/linux_display_amd64_177.80.html)

More news to come....  Alberto repacks.


> Release Highlights

    * Added support for the following new GPUs:
          o GeForce GTX 260
          o GeForce GTX 280
          o GeForce 9800 GTX+
          o GeForce 9800 GT
          o GeForce 9700M GTS
          o GeForce 9500 GT
          o GeForce 8100P
          o nForce 780a SLI
          o nForce 750a SLI
          o Quadro FX 770M
          o Quadro NVS 160M
          o Quadro NVS 150M
    * Improved support for RENDER masks, as well as RENDER repeating modes and transformations, for video memory pixmaps.
    * Added accelerated support for RENDER convolution filters for video memory pixmaps on GeForce 8, 9 and GTX GPUs.
    * Improved support for RENDER operations with the same source and destination; this should performance in some situations, e.g. when dragging Plasma applets in KDE4.
    * Improved GPU video memory management coordination between the NVIDIA X driver and OpenGL implementation; this should improve performance with e.g. the KDE4 OpenGL compositing manager.
    * Added an 'AllowSHMPixmaps' X configuration option, which can be used to prevent applications from using shared memory pixmaps; the latter may cause some optimizations in the NVIDIA X driver to be disabled.
    * Fixed a text rendering performance regression that affected GeForce 6 and 7 series GPUs.
    * Fixed a regression that caused the 'Auto' SLI X option setting to not enable SLI.
    * Fixed a bug that caused system hangs when using the NV-CONTROL interface to change GPU clock frequencies.
    * Added support for DisplayPort display devices (including 30-bit devices).
    * Resolved various stability problems on GeForce 8, 9 and GTX GPUs, as well as some GeForce 6 and 7 PCI-E GPUs.
    * Fixed a bug that resulted in GPU errors when changing the TwinView display configuration while using Compiz.
    * Further improved the error recovery paths taken in case of GPU command stream corruption.
    * Updated mode validation, in cases when no EDID is detected, such that 1024x768 @ 60Hz and 800x600 @ 60Hz are allowed, rather than just 640x480 @ 60Hz.
    * Removed an old workaround that caused incorrect Xinerama information to be reported after enabling a second TwinView display.
    * Fixed corruption when using SLI in SFR mode with OpenGL-based composite managers.
    * Fixed the subpicture component order reported by the NVIDIA X driver's XvMC implementation.
    * Added a workaround for broken EDIDs provided by some Acer AL1512 monitors.
    * Fixed a bug that caused GLXBadDrawable errors to be generated when running more than one OpenGL application with anti-aliasing enabled on GeForce 6 and 7 GPUs, e.g. wine.
    * Fixed a problem that could result in IRQs being disabled on some multi-GPU SMP configurations.
    * Worked around cache flushing problems (on some Linux kernels) that caused corruption and stability problems.
    * Added experimental support for PCI-E MSI.
    * Fixed a bug that resulted in AGP FW/SBA settings and overrides being applied incorrectly when using the Linux kernel's AGP GART driver.
    * Improved compatibility with recent Linux 2.6 kernels.
    * Updated the X driver to consider /sys/class/power_supply when determining the AC power state.

---

### Post by xebian on 2008-10-07
> **plun said:**
> This is how I sorted this out....

The failsafe options comes up  > choose to start in low graphics

Login screen comes up >  switch to the tty and stop gdm

Install driver > Restart gdm....  (edit or kdm...)


(I switched directly the first time and then I got a x-session which was impossible to kill and impossible to install a driver)

Maybe I'll try the final.

---

### Post by puntarenas on 2008-10-07
> **plun said:**
> News for "nVidia freaks"...   the driver is final  177.80


Good to see all the bugfixes and according to Phoronix the 2D performance problems are gone now: [Phoronix: NVIDIA 177.80 Display Driver](http://www.phoronix.com/scan.php?page=article&item=nvidia_17780&num=1)
I fear it is too late for Intrepid, although especially KDE-Users would benefit a lot. Someone in the mood to file a bugreport about the new upstream release? ;)

---

### Post by plun on 2008-10-07
Well, its already a ongoing process....

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/275098](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/275098)

---

### Post by puntarenas on 2008-10-07
Thank you, good to hear. :)

---

### Post by FuturePilot on 2008-10-07
Does the .80 fix the visual corruptions bug?

---

### Post by xebian on 2008-10-07
> **plun said:**
> Well, its already a ongoing process....

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/275098](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/275098)

177.80 && 27-6 is now working as good as my 177.78 && 27-5.  My KDE4 desktop effects are awesome.:guitar:

---

### Post by autocrosser on 2008-10-08
Looks like he got it thru freeze--I saw it in pending builds this morning!!!!

---

### Post by philinux on 2008-10-08
177.80 : I've been using all day it came through the updates about midday.

---

### Post by FuturePilot on 2008-10-08
Ugh. The corruption issue seems to be worse with the .80 driver. :(

---

### Post by canabal on 2008-10-08
This new driver is HORRIBLE.

I have been using intrepid since sunday and had no problems, but with the new version, every time I go to a screen in firefox that has any pictures, if I Page down, it looks as if nothing has changed, but then if I click the down button from there the screen will appear (or if I roll over any links that change colour with the mouse, they will appear).

---

### Post by FuturePilot on 2008-10-08
> **canabal said:**
> This new driver is HORRIBLE.

I have been using intrepid since sunday and had no problems, but with the new version, every time I go to a screen in firefox that has any pictures, if I Page down, it looks as if nothing has changed, but then if I click the down button from there the screen will appear (or if I roll over any links that change colour with the mouse, they will appear).

Yep, that's what I'm talking about. The bug is [here]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904")

---

### Post by plun on 2008-10-08
Within nVidias forum we can see users from all distributions discuss


[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

Firefox tabs
[http://www.nvnews.net/vbulletin/showthread.php?t=120735](http://www.nvnews.net/vbulletin/showthread.php?t=120735)


One important issue is to remove the **Flash beta **and use Flash RC and its coming tonight from repo.:)

I have perfect graphic, never seen better.

Also using **Adblock Plus** for Flash-ads removal !!!

---

### Post by canabal on 2008-10-08
just updated to the newest flash (just came through in the repos) and still no better.

---

### Post by | MM | on 2008-10-08
Hi,

I was wondering do we still have to run:
```
nvidia-settings -a InitialPixmapPlacement=2
```

Or is this on by default in the latest driver?

---

### Post by dabl on 2008-10-08
> **plun said:**
> 

I have perfect graphic, never seen better.



Yeah, me too -- 177.80 is looking really great here.  :guitar:

---

### Post by caryb on 2008-10-08
I had the NVidia Propriety driver installed (.80) after today's updates I have lost my 3D graphics & have this error!

root@stinkpad:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  nvidia-glx-177
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/15.4MB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 173855 files and directories currently installed.)
Preparing to replace nvidia-glx-177 177.76-0ubuntu1 (using .../nvidia-glx-177_177.80-0ubuntu1_amd64.deb) ...
Unpacking replacement nvidia-glx-177 ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-177_177.80-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/xorg/modules/extensions/libglx.so', which is also in package xserver-xorg-core
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-177_177.80-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Cary

---

### Post by dabl on 2008-10-08
@cary, you can just download it and use the installer. Do it like this:

[http://kubuntuforums.net/forums/index.php?topic=3098047.0](http://kubuntuforums.net/forums/index.php?topic=3098047.0)

:)

---

