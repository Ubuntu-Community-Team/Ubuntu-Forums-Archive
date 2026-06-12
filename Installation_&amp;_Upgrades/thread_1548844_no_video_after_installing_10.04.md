---
title: "no video after installing 10.04"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by bcharlessr on 2010-08-09
I attempted to install 10.04 on my dell studio XPS435MT and cannot get the video to display properly (blank screen). I do get the green light on my monitor but it shows nothing. I ran the 64 bit installer and installed alongside Windows Vista 64bit. 
 
Initially I could not get the installer to show any video. I was able to change to **nomodeset** to get the installer to run, but after the installation completed and I reboot into Ubuntu, I get no display. 
 
I have the ATI Radeon HD4670 video card with the DVI cable connected to the DVI port of my Dell S2409W HD monitor. When I now boot into Ubuntu I can hear the startup sound so I know it is booting, but cannot get any video to display. I also cannot boot to recovery mode with video. I have tried to add vga=xxx to the boot commands, but still nothing. I can see the grub menu and can still log into Vista with no problems.I also cannot CTL-ALT-F anything.
 
I am wondering if it is the DVI out that is causing this issue, (which would suck) or if any one else has had a similar issue?
 
BTW; I have not tried to hook up to the standard VGA port yet, which I think may resolve the issue. (because I am in denial, and because it would be a nightmare to change the cable back with the way my desk is setup currently). Also, if it is the problem I would rather try to resolve it than to have to succumb to the lesser quality video. 
 
I did find info on installing the ATI drivers, but am unsure on how to do it from the grub menu, since I cannot see anything when I boot.
 
While waiting, I tried to reinstall again, utilizing the partitions created the first time, and am having the same problem. I also checked the BIOS settings to see if there was something possibly there that would be causing the problem, but found nothing obvious.

---

