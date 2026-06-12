---
title: "Xorg requires &quot;nomodeset&quot; to avoid freeze at startup (xorg-video-intel)"
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by goebbe on 2010-02-18
On Lucid with latest updates the only way I can boot my computer is by adding the "nomodeset"-option in Grub. 
This is probably due to problems with the intel-video driver.
The same computer booted without problems on Ubuntu 9.10. 

It seems that the system freezes the moment X tries to start. The only way to recover is by hard reset (or REISUB).

If somebody else observes this bug, please confirm my bug report on launchpad: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/522940](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/522940)

---

### Post by code850 on 2010-02-18
I have exactly the opposite with intel 855gm chipset. My system freezes during boot when kernel mode setting is disabled.

---

### Post by goebbe on 2010-02-18
@code850: apparently this problem depends on the intel chipset. 

The comments on the bug-report suggest that UMS (user mode setting) should be disabled in the latest video-intel driver. This makes me really wonder why in some cases "nomodeset" works but the default KMS (kernel mode setting) does not. (If anything it should be the opposite)

---

### Post by timosha on 2010-02-18
> **code850 said:**
> I have exactly the opposite with intel 855gm chipset. My system freezes during boot when kernel mode setting is disabled. 

Same here on my Thinkpad with 855GM, system freezes during boot. I tried to use nomodeset in Lucid as this solves my hibernate/suspend problem in Karmic. Unfortunately, this doesn't work in Lucid.

---

### Post by code850 on 2010-02-18
Lucid manages somehow to unleash the full mighty of linux mysteries. Update after update new bugs appear and existing packages get broken. As per today's update firefox got broken. It's therefor time for me to purge gnome-update;)

---

