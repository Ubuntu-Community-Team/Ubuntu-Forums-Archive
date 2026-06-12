---
title: "Booting Problem: Toshiba Satellite Windows 10 Upgrade"
date: 2016-03-09
forum: Installation &amp; Upgrades
---

### Post by jospph on 2016-03-09
I have a Toshiba Satellite laptop with W10 upgrade.  My problem is that I can boot to the USB drive, and it will show the boot menu from the USB drive but it will not show anything but a black screen afterwards.  Any thoughts?

---

### Post by Bucky Ball on 2016-03-10
Welcome. 

Confused. You boot what from the USB drive? Ubuntu installer? Which version/flavour? Have some suggestions once confirmed, but if you are trying to boot Ubutnu, try this.

Boot the USB,
When you get to the purple screen with the icon down the bottom, hit a key,
When at the options, hit F6,
Choose 'nomodeset' from the menu that pops up,
Continue to 'Try Ubuntu'.

---

### Post by oldfred on 2016-03-10
Is it an upgrade from Windows 7 so probably BIOS boot?
Or an upgrade from Windows 8 so UEFI boot?

You want to boot Ubuntu live installer in same boot mode as Windows install. As Ubuntu installs in mode you boot install media and you really want all systems booting in same boot mode.

---

### Post by jospph on 2016-03-10
When I make my selection I get nothing but a black screen.

---

### Post by jospph on 2016-03-10
Oh and it is Ubuntu 12.04

---

### Post by Bucky Ball on 2016-03-10
> **oldfred said:**
> Is it an upgrade from Windows 7 so probably BIOS boot?
Or an upgrade from Windows 8 so UEFI boot?



And? We can't help you if you don't help us. Please address oldfred's questions so he can help.

---

### Post by jospph on 2016-03-10
Okay, before I continue to go into any more details of my issue:

I apologize for the duplicate post.  I'm new so I didn't exactly know if I would see replies in my notifications/email or not (which I did not from either.  I know now how to check them)

[B]Reply to 'oldfred'-
[/B]It was an upgrade from Windows 8.1 (that's all I know)

---

### Post by jospph on 2016-03-10
Yes, it is UEFI boot.

---

### Post by oldfred on 2016-03-11
Make sure Windows fast start up is off.
       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold

[/URL]
Do you know what video you boot with Intel, AMD, nVidia?
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size 

[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by jospph on 2016-03-12
It is AMD

---

### Post by oldfred on 2016-03-13
If newer UEFI, much better to use newest version of Ubuntu, or 14.04.4, 15.10 or if just experimenting even 16.04. the 16.04 will not be released until April but has many updates that make very new hardware work without extra effort.

For AMD you may find lots of instructions to install fglrx driver, do not install it. Open source driver works for most.
 With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
The fglrx driver is now deprecated in 16.04, use radeon and amdgpu

---

### Post by jospph on 2016-03-16
I fixed it! I just changed the sleep setting in the bios screen and, BAM! It worked &#128521;
Thank y'all for your help!

---

### Post by Bucky Ball on 2016-03-16
Excellent. Please see the first link in my signature below and mark thread as solved to help others. Good luck.

---

