---
title: "Yet another GRUB question"
date: 2006-03-29
forum: Installation &amp; Upgrades
---

### Post by uzd4ce on 2006-03-29
Sorry for yet another GRUB question, but I couldn't find a good answer for my problem elsewhere.

My machine has two hard drives; one SATA, one IDE.  WinXP is installed on the SATA, am trying to install Ubuntu on a partition on the IDE.

Installation seems to go fine.  I get to the point where it says that it detects WinXP installed on the computer, and if that's the only other operating system, it should be ok to install GRUB to the master boot record of hd0.  I let it.

At the next step it says it needs to reboot to finish installing components.  I remove the install cd and let it reboot, but it always goes straight into Windows, and never finishes the Ubuntu install.  Subsequent reboots always go straight to Windows.

Obviously, I'm a Linux novice, so any advice would be appreciated.  

Thanks

---

### Post by rplantz on 2006-03-29
If you go to the thread [http://www.ubuntuforums.org/showthread.php?p=871538](http://www.ubuntuforums.org/showthread.php?p=871538) and look at my post (#5), you may get some hints.

Do you have a live Ubuntu CD? You might be able to use that to run fdisk and get a better idea of what to name things.

I worked on this problem quite a bit. I'm not an expert in this, but I managed to get things to work. Keep us posted on your progress. I have to run an errand for a few hours, but if you don't get it working, I may be able to contribute more.

---

