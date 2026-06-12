---
title: "Can't install Broadcom STA Wireless Driver"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mike_IronFist on 2009-10-02
Just made a fresh install of the Karmic Beta today. While the servers must be going nuts (my NVIDIA driver is taking forever to download) I haven't been able to even BEGIN installing the Broadcom Wireless STA driver that I need so desperately with my laptop - unfortunately it's bound to a wired ethernet connection right now. What follows is the reason why:

When I open hardware drivers, my hardware and the necessary proprietary drivers for it are listed. Hooray. However, I click "activate" for the Broadcom Wireless STA driver, and then I authenticate it, but the authentication window doesn't close! I try to click "Authenticate", nothing, I click "cancel", nothing. I click the X and it closes... but of course my driver doesn't start installing. With my NVIDIA drivers, at least if I clicked the X it would close and start downloading the drivers...but the Broadcom drivers don't even attempt to install once I close the annoying authentication box!

Is there a way to install these drivers via command line so I don't deal with the super-faulty GUI?

---

### Post by novafluxx on 2009-10-02
> **Mike_IronFist said:**
> Just made a fresh install of the Karmic Beta today. While the servers must be going nuts (my NVIDIA driver is taking forever to download) I haven't been able to even BEGIN installing the Broadcom Wireless STA driver that I need so desperately with my laptop - unfortunately it's bound to a wired ethernet connection right now. What follows is the reason why:

When I open hardware drivers, my hardware and the necessary proprietary drivers for it are listed. Hooray. However, I click "activate" for the Broadcom Wireless STA driver, and then I authenticate it, but the authentication window doesn't close! I try to click "Authenticate", nothing, I click "cancel", nothing. I click the X and it closes... but of course my driver doesn't start installing. With my NVIDIA drivers, at least if I clicked the X it would close and start downloading the drivers...but the Broadcom drivers don't even attempt to install once I close the annoying authentication box!

Is there a way to install these drivers via command line so I don't deal with the super-faulty GUI?

I had to install my Broadcom drivers from the disc after installation, they weren't installed during installation...

---

### Post by Mike_IronFist on 2009-10-02
> **novafluxx said:**
> I had to install my Broadcom drivers from the disc after installation, they weren't installed during installation...

Yeah, well during the live cd boot, I was able to get the Broadcom drivers working straight from the CD... but when actually booted from my harddrive, no dice! Strange, huh? Yet then wierdest of all, after several seemingly failed attempts to try and get the update manager to even ATTEMPT to install the wireless drivers, I installed the NVIDIA drivers and now my wireless works.

It's a beta release, so I guess that means go figure!

---

### Post by dinxter on 2009-10-02
$sudo apt-get install bcmwl-kernel-source
will install the broadcom STA driver, maybe someone else knows whether it needs and post-install setup

[EDIT] just to add, i'm assuming your device is covered by the versions below

These package contains Broadcom 802.11 Linux STA wireless driver
for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and
BCM4322-based hardware.

---

### Post by Grimhound on 2009-10-02
> **dinxter said:**
> $sudo apt-get install bcmwl-kernel-source
will install the broadcom STA driver, maybe someone else knows whether it needs and post-install setup

[EDIT] just to add, i'm assuming your device is covered by the versions below

These package contains Broadcom 802.11 Linux STA wireless driver
for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and
BCM4322-based hardware.

Just isn't working for me. Now I have to hope this Windows 7 disc will install, as I need an operating system with internet access for school tomorrow and Ubuntu is now completely removed as an option due to Broadcom wireless support no longer working correctly. This happens every time I try to use the operating system.

---

### Post by alexmurray on 2009-10-02
I had the same problem with Alpha 4 when I installed it: [http://ubuntuforums.org/showpost.php?p=8008119&postcount=12](http://ubuntuforums.org/showpost.php?p=8008119&postcount=12) - see if that helps you - basically it seems you *may* need to try installing / removing the driver a couple times till it finally works....

---

### Post by Grimhound on 2009-10-02
Anyone have any other methods I could attempt in an effort to get the drivers installed and working? Hope this issue is resolved soon. @.@;

---

### Post by Grimhound on 2009-10-02
> **alexmurray said:**
> I had the same problem with Alpha 4 when I installed it: [http://ubuntuforums.org/showpost.php?p=8008119&postcount=12](http://ubuntuforums.org/showpost.php?p=8008119&postcount=12) - see if that helps you - basically it seems you *may* need to try installing / removing the driver a couple times till it finally works....

Oh my gosh, thanks so much. Here, this is for you. :D

[IMG]http://imgur.com/P1Jfv.jpg[/IMG]

---

