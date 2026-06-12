---
title: "Kubuntu feisty install from liveCD failed, grub broken"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by merike on 2007-10-21
My install hung completely so I rebooted. Now I'm unable to use liveCD desktop since it won't load correctly and grub is broken with error 22 too. But I can get to liveCD-s commandline.
Is there anything to try except burning new cd (this one had no errors yet it didn't work) or try alternate installer (it was the working solution for Edgy install on my computer, even though it didn't write some network conf correctly)?

---

### Post by Pumalite on 2007-10-21
You might try reinstalling Grub (though I doubt it)
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
You might have to reinstall. Use Alternate CD
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by merike on 2007-10-21
I got impatient and got Gutsy alternate. Install was ok and grub is fine, but I'm having issues with x-server. I suppose I need a new thread.

---

### Post by Pumalite on 2007-10-21
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

