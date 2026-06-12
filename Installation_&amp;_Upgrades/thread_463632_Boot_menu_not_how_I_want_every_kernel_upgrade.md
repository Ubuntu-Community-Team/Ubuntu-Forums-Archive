---
title: "Boot menu not how I want every kernel upgrade"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by nightmareci on 2007-06-03
When I installed Ubuntu 7.04, I had my computer set to only have the hard drive that Ubuntu being installed on was plugged in, so I wouldn't risk mucking up my Windows XP installation on a separate internal hard disk (I had issues with disk booting at that time... those issues are gone now), so I could later have a dual-boot system. However, on each kernel upgrade, because Ubuntu was installed with a setup not including any other operating system, the boot menu must be manually edited on each kernel upgrade to allow easy booting of Windows XP (I have it at the top of the list, so everyone around not wanting Linux can easily use Windows XP). I want to know what I must modify so that the menu list is updated with the Windows XP boot entry included. Also, kernel upgrades cause the boot entries to have the wrong hard drive for where Ubuntu is (it sets to (hd1,0) when it should be (hd0,0) to boot, I believe). This is merely an annoyance, no critical issue, but I'd very much like to fix this issue with my system. (I think this goes here, because it involves an issue whenever I get kernel upgrades, but if I'm wrong, go ahead and move the thread.)

---

### Post by mystman on 2007-06-03
Yeah, it does that to me too.  I just changed it back and made a back up in my home directory.  Whenver there's a new kernel I put in the new kernel args in the boot section for ubuntu and reload my backup.  That's really all you can do about it.

---

### Post by confused57 on 2007-06-03
> **nightmareci said:**
> When I installed Ubuntu 7.04, I had my computer set to only have the hard drive that Ubuntu being installed on was plugged in, so I wouldn't risk mucking up my Windows XP installation on a separate internal hard disk (I had issues with disk booting at that time... those issues are gone now), so I could later have a dual-boot system. However, on each kernel upgrade, because Ubuntu was installed with a setup not including any other operating system, the boot menu must be manually edited on each kernel upgrade to allow easy booting of Windows XP (I have it at the top of the list, so everyone around not wanting Linux can easily use Windows XP). I want to know what I must modify so that the menu list is updated with the Windows XP boot entry included. Also, kernel upgrades cause the boot entries to have the wrong hard drive for where Ubuntu is (it sets to (hd1,0) when it should be (hd0,0) to boot, I believe). This is merely an annoyance, no critical issue, but I'd very much like to fix this issue with my system. (I think this goes here, because it involves an issue whenever I get kernel upgrades, but if I'm wrong, go ahead and move the thread.)

You need to change the #groot entry in your /boot/grub/menu.lst to (hd0,0).

Copy & paste your Window's entry just  above the line ###BEGIN AUTOMAGIC KERNELS LIST...

---

