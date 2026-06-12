---
title: "installed wrong grub"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by youbaji on 2010-04-09
Hello all,
I have ubuntu 8.04LTS and winxp on the same hard drive.  I intended to reinstall grub after windows installation.  I couldn't find my 8.04 disk so I used ubuntu 9.10 livecd and executed "grub-install /dev/sda".  Then I realized I installed a different grub.  After reboot, I had a "grub>" command line.  I typed in same commands in my correct "/boot/grub/menu.lst" for booting ubuntu.  The system started to boot for a few seconds and rebooted.  
So, is this a kernel problem or a grub problem?
Is there a way to correct this?

Thanks!

---

### Post by oldfred on 2010-04-09
To be sure of what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by youbaji on 2010-04-09
Thank you for your suggestions.
I have solved the problem.  It is a grub problem.  I installed an older version of grub and the problem is gone.

---

