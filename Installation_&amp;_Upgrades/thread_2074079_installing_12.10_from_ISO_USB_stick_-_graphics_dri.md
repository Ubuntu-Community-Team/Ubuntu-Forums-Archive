---
title: "installing 12.10 from ISO USB stick - graphics driver problem"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by Ross Gayler on 2012-10-20
Hi,

I am attempting to install Ubuntu 12.10 64-bit desktop from the install ISO on a USB stick to an HP 8540w laptop. The installer boots and shows the purple ubuntu splash screen with the loading progress indicator.  However, when it gets to the part where I would expect the graphical installer interface to be displayed the screen gets corrupted (mostly white with a scattering of geometric hash patterns). After a while it falls back to a text screen that gives some error messages like:

[drm] nouveau ... Failed to idle channel 2
[drm] nouveau ... PGRAPH TLB flush idle timeout fail: ...

Then it cycles through <corrupted screen> <error messages>.

I presume this is a problem with the nvidia graphics hardware and the driver.  Is there some way to modify the boot parameters in the installation ISO so that it sticks with a safe graphics mode during installation?

Or maybe the issue is something else entirely.  All suggestions gratefully received.

Thanks

---

### Post by arpanaut on 2012-10-20
During testing of quantal the users with nvidia cards were having success booting by removing "splash" from the boot parameters, when confronted with corrupted graphics.

When booting the live desktop iso, immediately after the first purple screen appears, and the little man and keyboard icon appears hit any key, choose language, and I think accept one other thing by hitting enter, you will see some choices, ignore and hit f6 then change the boot parameter, removing splash, continue to boot to the live desktop and do the install.

The first time booting from the installed OS, when you see the grub menu hit "e" and edit the boot parameters removing splash again, "ctrl x" to boot to the desktop then install the nvidia driver and you should be good to go.

I was under the impression this was fixed for the final release, but maybe not for all hardware,

Hope this helps...

---

### Post by Ross Gayler on 2012-10-21
Thanks. (BTW my screen resolution was so poor that I didn't recognise the little man and keyboard icons until after reading your description.)

I have progressed. I was able to install 12.10 (interestingly the install process seemed to have the graphics set correctly even though the system it installed was in some clunky graphics mode). I tried installing the first proprietary nvidia driver (current) - but that caused problems (wallpaper displayed but no user interface bars).  I'll have to sort that out next, but I've run out of weekend.

---

### Post by oldfred on 2012-10-21
There is a bug on installing proprietary drivers. The headers are missing, so you need to install those first, then your driver.

Fix for nVidia with 12.10 missing kernel dpkg reconfigure:
[http://ubuntuforums.org/showthread.php?t=2072862](http://ubuntuforums.org/showthread.php?t=2072862)

cntrl-alt f1 or f2 to get to terminal also works
sudo apt-get install linux-headers
sudp apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo dpkg-reconfigure nvidia-current
(Same for fglrx also)
sudo apt-get install linux-headers-generic fglrx-updates


Has most bug reports:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341)

[https://bugs.launchpad.net/fglrx/+bug/1068456](https://bugs.launchpad.net/fglrx/+bug/1068456)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)
[https://bugs.launchpad.net/fglrx/+bug/1068661](https://bugs.launchpad.net/fglrx/+bug/1068661)

Has what worked for me, install headers & dpkg update.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942)

When you see you are in the desktop but no icon or bar, right click to change desktop background
When the window appear, click all settings, now you see the system settings window.
Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia or AMD... fglrx-upgrade

---

