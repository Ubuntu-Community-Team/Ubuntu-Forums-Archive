---
title: "Resolution stuck at 1024x768 after Natty upgrade"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by gdanko on 2011-06-22
I performed an upgrade from 10.something, whichever is the "m" version to Natty via the command line on an HP Compaq dc5700. After the install and reboot I saw an error about the video card not being compatible with Unity and dumping me to 1024x768.

There is no xorg.conf on the system and I cannot seem to get into single user mode to try and configure one because grub does not appear.


[10:30:40 root@becameship rc5.d]# lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

I am at a loss here.

---

### Post by Blasphemist on 2011-06-22
On this page you'll see a command you can run that will tell you if you can run Unity and if not, why.
[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)
```
/usr/lib/nux/unity_support_test -p
```

Please see this and more in this thread, starting with post 1.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
> Intel i915GM
There is a known bug with this chipset and Natty. Some of the workarounds include using "i915modeset=0" and some "i815modeset=1" in the kernel boot line and going to /etc/default/grub to 
Quote:
Andy Whitcroft wrote on 2010-12-02 as part of Launchpad Bug [https://bugs.launchpad.net/ubuntu/+s...x/+bug/683775:](https://bugs.launchpad.net/ubuntu/+s...x/+bug/683775:) 

As a work-around we can turn this off by adding the line below to /etc/default/grub and running update-grub:
GRUB_GFXPAYLOAD_LINUX=text
There is also an upstream Debian Bug with this driver that says if you try to use a "vga=xxx" switch on a Linux 2.6.x kernel and this driver, you will get a black screen. It further says if you use anything besides the i915's driver's internal framebuffers, it will get a black screen. So-- the "i915modeset=0" also has to be set in the kernel boot line to turn off KMS.


---

### Post by gdanko on 2011-06-23
> **Blasphemist said:**
> On this page you'll see a command you can run that will tell you if you can run Unity and if not, why.
[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)
```
/usr/lib/nux/unity_support_test -p
```

Please see this and more in this thread, starting with post 1.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

That command did not exist on my Natty install for some reason.

Anyway, there was no xorg.conf so I created one based on the hardware I have and I seem to be up and running now, back at 1920x1200.

---

