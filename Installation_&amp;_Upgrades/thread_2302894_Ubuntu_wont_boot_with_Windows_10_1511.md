---
title: "Ubuntu wont boot with Windows 10 1511"
date: 2015-11-14
forum: Installation &amp; Upgrades
---

### Post by Victor_Gnanaraj on 2015-11-14
Hi all,

I did a clean install of windows 10 1511 (threshold 2) and then tried to dual boot ubuntu 15.10.(dual boot previously worked fine with Windows 10 first official release). But now after i install ubuntu i can see grub, but once i logged into windows using grub thats it, windows somehow removes grub and i can no longer see it during boot(windows automatically boots up). I tried using easy bcd tool to manually add, but even that option is not supported in EFI mode. :(

can someone help me

---

### Post by grahammechanical on 2015-11-14
Just to be clear

You installed Windows 10 and then installed Ubuntu? Or the clean install of Windows 10 wiped out an existing install of Ubuntu? Did you install Windows 10 in EFI mode and then install Ubuntu in legacy mode?

It seems to me that your thread title is wrong. It is Windows 10 that is preventing you from loading Ubuntu. Please provide a screen shot of a Windows 10 utility that shows the layout of the hard disk partitions. Please run a Ubuntu live session and install Boot Repair and create the boot info report and post the URL to that report in this thread.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

EDIT: this more recent thread might be relevant

[http://ubuntuforums.org/showthread.php?t=2302919](http://ubuntuforums.org/showthread.php?t=2302919)

---

### Post by mehdimzg on 2016-06-01
> **Victor_Gnanaraj said:**
> Hi all,

I did a clean install of windows 10 1511 (threshold 2) and then tried to dual boot ubuntu 15.10.(dual boot previously worked fine with Windows 10 first official release). But now after i install ubuntu i can see grub, but once i logged into windows using grub thats it, windows somehow removes grub and i can no longer see it during boot(windows automatically boots up). I tried using easy bcd tool to manually add, but even that option is not supported in EFI mode. :(

can someone help me

Hi Victor,

I also noticed the problem! Apparently the problem is caused by a new Microsoft Patchfrom May 2016! Windows 10 seals all Partitions when turning in (Hypernation mode) sleep mode !! So I use folwing workaround  wehn shutdown windows 10 V1511:  I hold fast the key Shiff over ctRL and click Shutdown. 
Probably related sealed windows in sleep mode Linux Ext partition! And therefore, the booter from Grub not do his service! I think it helps if you first windows shutdown completely until Linux community to find a solution, because Microsoft has probably installed the problem intentionally !!!

---

### Post by SnazzleLabsYT on 2016-06-01
It is fast startup to blame. Navigate to: Control Panel > Power Options > on the left, there is a button that says 'Require a password on wakeup'. This will get us to the place to disable fast startup. > 'Change settings that are currently unavailable' > uncheck 'Turn on fast startup'. This should fix your problem.

---

