---
title: "Is Ubuntu Minimal Compatable with Nvidia Drivers?"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by TripleD on 2013-11-30
Is there an extra step one must take to get Nvidia drivers (or perhaps any graphics drivers) working with Ubuntu Minimal?

A few weeks ago I was rebuilding my system from the ground up. I installed 13.10 minimal with only the SSH and Samba File Server options. So far so good. Then I tried adding "nvidia-current". Black screen. Still no worries; this was far from the first black-screen/Nvidia-driver issue I've had with Linux.

That's when things got ugly. I tried every trick I've done in the past. I tried blacklisting nouveau. I tried downloading and installing the drivers manually. I tried 3rd party ppa's. Nothing worked.

Just for the purpose of logical troubleshooting, is there something that has changed about Ubuntu Minimal? Some package or option at installation that must be selected to get a graphic driver working?

Thank you for any help you can offer?

---

### Post by ian-weisser on 2013-11-30
There is no secret difference or change between the kernel and system tools in the Minimal .ISO and the Desktop or Server .ISO images.

---

### Post by papibe on 2013-11-30
Hi TripleD.

A few thoughts:

Which DE did you install? In order to have a working GUI you need first a desktop environment.

Have you tried setting the nomodeset option? If not try it. [Her's]("http://ubuntuforums.org/showthread.php?t=1613132") how.

Could you also post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here [paste.ubuntu.com]("http://paste.ubuntu.com/"), and then post back the link.

Regards.

---

### Post by TripleD on 2013-12-01
Sorry for the late reply (friend's birthday/hangover/live in China)

> **ian-weisser said:**
> There is no secret difference or change between the kernel and system tools in the Minimal .ISO and the Desktop or Server .ISO images.

I figured that was still true. Just wanted to make sure ("once you've eliminated all the possible" and so on).

[QUOTE=papibe]
Which DE did you install? In order to have a working GUI you need first a desktop environment.
[/QUOTE]

At the moment, none. My order of installation was:
1) Ubuntu minimal
2) NVIDIA Driver
3) XBMC
4) Wine/Winetricks
5) Steam

I'm pretty sure getting steam to run will require GNOME or something similar, but I figured I'd cross that bridge when I get to it.

[QUOTE=papibe]
Have you tried setting the nomodeset option? If not try it. [Her's]("http://ubuntuforums.org/showthread.php?t=1613132") how.
[/QUOTE]

Not yet, but I'll give it a whirl

[QUOTE=papibe]
Could you also post the content of this file?
```
/var/log/Xorg.0.log
```
[/QUOTE]

Here's the full log file: [http://paste.ubuntu.com/6502925/](http://paste.ubuntu.com/6502925/)

If it's simpler though, here is the out put of "cat Xorg.0.log | grep NVIDIA": [http://paste.ubuntu.com/6502927/](http://paste.ubuntu.com/6502927/)

Thanks for the advice. I'll report back if the nomodeset idea works.

---

### Post by papibe on 2013-12-01
Thanks.

It looks like the Intel driver is also trying to get access to the display. I'm guessing you may have an [Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html") system.

Could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by TripleD on 2013-12-01
> **papibe said:**
> Thanks.

It looks like the Intel driver is also trying to get access to the display. I'm guessing you may have an [Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html") system.

Could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

You got it:
> 
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF110 [GeForce GTX 580] [10de:1080] (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:2550]
	Kernel driver in use: nvidia


Also, I tried modifying the default grub file to include "nomodeset". Normally the screen just goes to black, 
but this time it gave a "blink" or "flash" before going black. It's doing something, although what I'm not sure.

I checked the xorg log files, but it looks to be the same as before.

---

### Post by TripleD on 2013-12-01
facepalm.jpg

I forgot to run "sudo update-grub" after changing the grub file.

I can now get a nice shiny Ubuntu 13.10 loading screen and text console no problem. Still a black screen after that, but I think that is an xbmc issue.

Thanks for all of your help.

---

### Post by papibe on 2013-12-01
Glad you worked it out :)

---

### Post by oldos2er on 2013-12-02
> **TripleD said:**
> I'm pretty sure getting steam to run will require GNOME or something similar, but I figured I'd cross that bridge when I get to it.


Steam only requires X and a window manager, I know this because that's how I've been running it.

---

