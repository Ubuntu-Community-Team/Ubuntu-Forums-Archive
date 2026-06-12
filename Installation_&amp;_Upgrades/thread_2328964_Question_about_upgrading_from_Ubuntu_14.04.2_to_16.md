---
title: "Question about upgrading from Ubuntu 14.04.2 to 16.04.1"
date: 2016-06-26
forum: Installation &amp; Upgrades
---

### Post by tomdkat on 2016-06-26
Hi!  My mom runs Ubuntu 14.04.2 on her computer and I know I'll be able to upgrade it to 16.04.1 sometime in July or so.   In the meantime, I downloaded a 16.04 DVD ISO, burned it to a disc, and booted it on mom's computer to see what would happen.  The system started booting but the monitor lost the video signal (amber power light instead of blue or green) and I never saw any Ubuntu logos, etc.  This was with the UEFI boot.  So, I tried booting it without UEFI and I saw an Ubuntu screen (brown-ish color with some graphics at the very bottom) but eventually, the monitor lost signal and the screen went black and stayed black.  So, I never got a successful boot from the DVD.   I did manage to boot Linux Mint 17.3 from a DVD ISO I also downloaded and it booted just fine.

So, my question is:  if the 16.04 DVD didn't boot properly on my mom's computer, does this mean the upgrade to 16.04.1 will be problematic?

My mom's computer is a Gateway system with an AMD A6-5400K APU w/ integrated Radeon HD graphics.   The Gallium 0.4 driver is used for the integrated graphics "adapter".  Attached is a screen shot of the "About Ubuntu" window.

Thanks!

Peace...

---

### Post by banceu_sergiu_ione on 2016-06-26
Maybe. You have to check if with [BootOption selected acpi=off, noapic, nolapic]("https://help.ubuntu.com/community/BootOptions") it loud. If does and run good, then you'll have to set this in grub once you got the upgrade. Or go for a new install. Up to you. If struggle to run, then leave it on 14.04 or if you like consider Mate Ubuntu or Lubuntu.
You can try with nomodeset too if with acpi off not work. Nomodeset will run only on generic video driver.

---

### Post by tomdkat on 2016-06-28
Thanks for the tips.  I'll give the boot options a try and will see what happens.  Since starting this thread, I booted the same Ubuntu 16.04 on another system, a HP with an AMD A8-5500k APU and Radeon HD graphics and it booted just fine.   I'll also try booting from another optical drive to see what happens.

Thanks again!  :)

Peace...

---

### Post by grahammechanical on 2016-06-28
There are no AMD proprietary video drivers in 16.04. So, if the machine is not using an AMD driver then one little complication will be avoided.

> The fglrx driver is now deprecated in 16.04, and we  recommend its open source alternatives (radeon and amdgpu). AMD put a  lot of work into the drivers, and we backported kernel code from Linux  4.5 to provide a better experience. 


When  upgrading to Ubuntu 16.04 from a previous release, both the fglrx  driver and the xorg.conf will be removed, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware). 


More information is available at [https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/) 

 


[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Regards.

---

### Post by tomdkat on 2016-07-02
Ok, so I have an update on this.  :)   First, thanks for the responses and for the tips.  :)   

I booted the 16.04 liveDVD from another optical drive, a USB drive, with the same "black screen" result.  So, I booted the DVD from the internal optical drive and specified the "nomodeset" kernel option and voila, the system booted.   However, it booted at a low resolution (800x600 maybe).   I looked at the Xorg.0.log file and found this message, " *ERROR* No UMS support in
radeon module!".  So, I did some searching on that message and found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1568211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1568211)

A few others have experienced this issue as well.    I re-booted the Linux Mint liveDVD that worked and found it's using a 3.19.x version kernel vs Ubuntu 16.04 using a 4.4.21 version kernel.    With regard to the video driver, my mom's Ubuntu 14.0.4.2 install is using the "radeon" driver, not flgrx.

So, I'm not sure how to proceed, at this point.   I can either keep her on Ubuntu 14.04.2 for a while longer, or I can switch to another distro, of I can get another video card and see if that works any better with Ubuntu 16.04.

This is where things stand as of today.  :)

Thanks!

Peace...

---

### Post by kansasnoob on 2016-07-02
Trusty (14.04) is still supported until 2019. I'm keeping about 60 machines on Trusty because it's just rock solid.

---

### Post by grahammechanical on 2016-07-02
My 16.04 install is now at kernel 4.4.0-28-generic. So, the kernel has moved on since you downloaded that ISO image.

> graham@Ub1604:~$ uname -a
Linux Ub1604 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


I see your options as: (1) Remain on 14.04. (2) Wait until 16.04.1 is released and test that ISO image. (3) Look at the situation in a year's time.

Regards.

---

### Post by tomdkat on 2016-07-03
Thanks for the info on the kernel update.   At this point, I'll wait until 16.04.1 is released and I'll test that ISO.  I was asked to file a new bug report on this, and I'll see about doing that today.

Thanks again to everyone!  :)

Peace...

---

### Post by tomdkat on 2016-07-04
Well, I have another update on this issue.  I created this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1598935](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1598935)

and during the process of getting the requested info, I discovered I could get the live DVD to boot *without* specifying "nomodeset".  In fact, I'm posting this from the system booted from the 16.04 live DVD now.   It seems removing "quiet splash" from the kernel parameters and pressing "Ctrl-Alt-F1", then "Ctrl-Alt-F7" gets me access to the Unity desktop.  Pressing "Ctrl-Alt-F1" results in the monitor getting a video signal and pressing "Ctrl-Alt-F7" displayed the desktop.

Thanks again for your help!

Peace...

---

### Post by tomdkat on 2016-07-04
[duplicate post I can't seem to delete]

---

