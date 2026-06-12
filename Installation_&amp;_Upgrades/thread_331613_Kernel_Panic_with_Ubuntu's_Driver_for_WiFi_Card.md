---
title: "Kernel Panic with Ubuntu's Driver for WiFi Card"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by Slodeine on 2007-01-04
I've recently been experimenting with dual-booting Edgy Eft and Windows.  I first tried it on my Desktop with Windows 2000 and was impressed with the out-of-the-box compatibility I experienced with my admittedly disparate setup.  However, I share that computer with family members and dislike restarting whenever they need to use Windows.  So I shrunk the WinXP partition on my personal laptop and installed Ubuntu.  Again, I was impressed that Ubuntu recognized my wireless PCI card (Linksys WPC54G v1.2) out of the box, but I experience what I am told is called "kernel panic" whenever I attempt to use the card, or even configure it.  Additionally, Edgy Eft's drivers do not seem to provide full functionality.  

Believing my difficulties were driver-related, I spent several days on the forums, attempting to find alternate drivers.  I attempted to use ndiswrapper as well as bcm43xx to no avail.  Ultimately, I completely reinstalled Edgy Eft and attempted the solution outlined in [this]("http://ubuntuforums.org/showthread.php?t=185174") thread.  The bcm43xx driver seems to provide better functionality, but kernel panic still occurs.  In fact, it occurred in every solution I attempted.

I was advised to post the results of **dmesg**.  They are contained in [this]("http://home.comcast.net/~ksonnad/boot.mesg") file.  Keep in mind that these results were obtained *after* I installed and used bcm43xx to obtain different drivers.

Can anybody offer a solution?  Is any additional information required?

---

### Post by Slodeine on 2007-01-05
I hate to bump, but I could really use some help here.

---

