---
title: "Ubunto does not install"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Ganymedes on 2008-03-02
I am trying to install Ubuntu 7.10 (standard 32-bit) on a Pentium III, 1.0 Ghz computer with ASUS CUSL2-C ACPI motherboard (bios revision 1009). I am using factory defaults on the motherboard.

When I boot it from the CD, I get the first menu, but after selecting "install ubuntu" from there, I just get the "Loading Linux Kernel" form proceeding to 100% but nothing happens after that. It is like loading the kernel fails.

The computer runs happily Puppy Linux live-CD versions 2.17 and below and also Win2K and XP Pro.

I have also tried Ubuntu 6.06 version, which just give a blank screen on boot and Kubuntu 7.10 which gives exactly the same problem as Ubuntu 7.10, which is much expected of course. And yes, I tried "the alternate Ubuntu 7.10 version, too" which did not work any better.

Does anybody know if there is a hardware compatibility document somewhere and is this really something to be expected with Ubuntu with a bit older computers? I have previously successfully installed Ubuntu 7.10 on Vmware and on 64-bit Intel Core Duo2 laptop. Those installations did not have any problems.

---

### Post by jeffus_il on 2008-03-02
How much memory do you have?

---

### Post by Pumalite on 2008-03-02
256 MB of RAM or less>Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by Ganymedes on 2008-03-02
I have 512 Mbyte of memory.

I do have 3Dlabs Oxygen VX1 graphics adapter, which is not a very common card - does that really matter in the process of loading the kernel? ... I could try with something else, if feasible at all? I already tried with "safe graphcis mode" - the problem remains.

---

### Post by jeffus_il on 2008-03-02
Start here, it doesn't look too good but he could be wrong:
[http://ubuntuforums.org/showthread.php?t=670375](http://ubuntuforums.org/showthread.php?t=670375)

---

### Post by jeffus_il on 2008-03-02
This commercial driver may work:
[http://www.xig.com/Pages/HdweSupported/ChipINDEX.html](http://www.xig.com/Pages/HdweSupported/ChipINDEX.html)

It's listed here as well:
[http://www.xigraphics.com/Pages/Demos/DX-SilverLinux.html](http://www.xigraphics.com/Pages/Demos/DX-SilverLinux.html)

---

### Post by cmnorton on 2008-03-02
How much RAM is in the system? 

Did you try to install in safe mode?

Also, you might want to consider installing XUbuntu, because it uses less memory. The laptop I'm using to write this is a non-hyperthreaded PIV. It started with 256MB RAM, which I believe is the Ubuntu minimum. The system did not stop being sluggish until I upped the memory to 1GB (motherboard's max), stopping at 512 and 750MB RAM along the way.

---

### Post by Ganymedes on 2008-03-02
> **jeffus_il said:**
> Start here, it doesn't look too good but he could be wrong:
[http://ubuntuforums.org/showthread.php?t=670375](http://ubuntuforums.org/showthread.php?t=670375)

Thanks - actually, this is right on spot with my problem.

Yes, it was because of this 3dLabs Oxygen VX-1 graphics adapter - I changed that to a basic Matrox Millenium G400 - now it works OK.

Thanks also for the rest of the tips - they may help me with other systems later on :)

:popcorn:

---

