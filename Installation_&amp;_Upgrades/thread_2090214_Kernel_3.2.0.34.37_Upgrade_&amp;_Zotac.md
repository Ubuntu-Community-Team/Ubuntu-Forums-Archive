---
title: "Kernel 3.2.0.34.37 Upgrade &amp; Zotac"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by ThePol1 on 2012-12-01
I am running 12.04 (AMD_64). The latest kernel upgrade on my Zotac Atom 525-based machine results in my monitor going to sleep immediately on boot. I see the bios splash screen and the standard Ubuntu purple boot screen, but when it gets to the login screen it will not wake up. I can hear the standard Ubuntu 'login' sound and I can ssh into the machine, but there is no waking the monitor. Any thoughts?

I have my monitor connected via an HDMI to DVI connection. I have added nomodeset to my Grub menu, but that results in an unusable resolution of 640x480. Please help!

---

### Post by ThePol1 on 2012-12-02
> **ThePol1 said:**
> I am running 12.04 (AMD_64). The latest kernel upgrade on my Zotac Atom 525-based machine results in my monitor going to sleep immediately on boot. I see the bios splash screen and the standard Ubuntu purple boot screen, but when it gets to the login screen it will not wake up. I can hear the standard Ubuntu 'login' sound and I can ssh into the machine, but there is no waking the monitor. Any thoughts?

I have my monitor connected via an HDMI to DVI connection. I have added nomodeset to my Grub menu, but that results in an unusable resolution of 640x480. Please help!

To continue to troubleshoot this problem, I've disconnected and reconnected my hdmi video cable. This does not work. My monitor still goes to sleep as if there isn't any hdmi signal going to it. If anyone can shed some light for me, I'd appreciate it.

---

### Post by 2F4U on 2012-12-02
Can you provide more information about your hardware? What graphics card and driver did you use before the upgrade? There seem to be some problems with 12.10 and proprietary ATI and nVidia drivers, so that may be a possible source of your issues.

---

### Post by ThePol1 on 2012-12-02
> **2F4U said:**
> Can you provide more information about your hardware? What graphics card and driver did you use before the upgrade? There seem to be some problems with 12.10 and proprietary ATI and nVidia drivers, so that may be a possible source of your issues.

Thanks for the reply! I'm running Ubuntu 12.04.1 (AMD64). I don't have any proprietary drivers loaded. In terms of hardware:
Model	ZBOXSD-ID12-U
- Intel Atom D525 1.8 GHz Dual-Core
- Intel NM10 Express
- Intel GMA 3150

This is a link to the manufacturer's website:
[http://www.zotacusa.com/zbox-sd-id12.html](http://www.zotacusa.com/zbox-sd-id12.html)

---

### Post by ThePol1 on 2012-12-02
Here is some interesting notes from the logs. These messages do *not* appear when I boot with the older kernel.

Dec  2 14:44:13 nicaea kernel: [    2.709034] No connectors reported connected with modes
Dec  2 14:44:13 nicaea kernel: [    2.709034] [drm] Cannot find any crtc or sizes - going 1024x768

---

### Post by ThePol1 on 2012-12-04
I wasn't able to find an answer to this. I ended up upgrading to a newer machine with NVidia ION graphics:
[http://www.zotacusa.com/zbox-id41-plus.html](http://www.zotacusa.com/zbox-id41-plus.html)

---

