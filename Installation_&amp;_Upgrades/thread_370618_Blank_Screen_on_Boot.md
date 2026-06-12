---
title: "Blank Screen on Boot"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by bkeller81 on 2007-02-25
I have been running Ubuntu 6.10 on my older dell laptop for a few weeks. I have enjoyed my experience and decided to duel boot my desktop with XP and Ubuntu 6.10. I downloaded and attempted to boot the regular version that first loads into the Live CD. It would get to the point of loading with the orange bar going across the screen and then when it reaches 100% my screen goes blank. So i thought I would try the Alternate-Install version.

Went through the install just fine. Gets to the boot screen and lets me choose Ubuntu or XP. I choose Ubuntu and it appears as if it is going to load (same as live CD) and then at 100% the screen goes blank.

I have tried CTRL+ATL+F# with no luck, nothing happens. If I view the text while loading the only problem I see is that codec 0 failed to load, but I believe that is related to my sound card.

Please Help. Thanks In Advance

---

### Post by tgalati4 on 2007-02-26
It looks like a video problem.  The X server is trying to start with an unsupported video mode and goes blank as a safety measure.

Next time you boot Ubuntu, hit the escape key a few times to remove the splash screen and see what is going on.  What is the laptop model?

I am running Dapper on an older Dell Inspiron 7500.

Try booting into a rescue shell (it should be one of your Grub menu picks)

then type dpkg-reconfigure xserver.xorg

Make intelligent choices then startx to restart the server.

Edgy has some improved video features that may be incompatible with your video hardware, like 3D, and hooks for the compositing manager and improved video drivers.

Good luck.  Oh, and welcome to the community.

---

### Post by confused57 on 2007-02-26
> **bkeller81 said:**
> I have been running Ubuntu 6.10 on my older dell laptop for a few weeks. I have enjoyed my experience and decided to duel boot my desktop with XP and Ubuntu 6.10. I downloaded and attempted to boot the regular version that first loads into the Live CD. It would get to the point of loading with the orange bar going across the screen and then when it reaches 100% my screen goes blank. So i thought I would try the Alternate-Install version.

Went through the install just fine. Gets to the boot screen and lets me choose Ubuntu or XP. I choose Ubuntu and it appears as if it is going to load (same as live CD) and then at 100% the screen goes blank.

I have tried CTRL+ATL+F# with no luck, nothing happens. If I view the text while loading the only problem I see is that codec 0 failed to load, but I believe that is related to my sound card.

Please Help. Thanks In Advance
Someone might be able to help you, but you need to post the specs of your desktop, e.g. video card(brand, PCIe), monitor(DVI or VGA), etc.

---

### Post by bkeller81 on 2007-02-26
Thanks for the help.  
Here are my System Specs:
MoBo: ASUS KV8
Processor: AMD 64 3200+
Video Card: ATI RADEON 9800 PRO
Monitor: Sony SDM-S73 (VGA)
[INDENT]Resolution: 1280 x 1024 Maximum
Contrast Ratio: 500:1[/INDENT]

---

### Post by confused57 on 2007-02-26
Might be your video card, see if there is anything in this thread that might help:
[http://www.ubuntuforums.org/showthread.php?t=354041&highlight=blank+screen](http://www.ubuntuforums.org/showthread.php?t=354041&highlight=blank+screen)

---

### Post by bkeller81 on 2007-02-27
well thanks to everyone.  I finally got it working now it is just a matter of updating my ATI drivers.  So glad to be in the Linux community!

---

### Post by tgalati4 on 2007-02-27
Glad to hear you are up and running.  A day with out Ubuntu is like a day with Windows.

Welcome back.

---

