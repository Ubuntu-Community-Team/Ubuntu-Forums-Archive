---
title: "Grub error 21"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Malletdude31 on 2010-01-26
So, a while back, i tried installing Ubuntu on a portable hard drive, because my computer (Thinkpad T41) had little memory, so a dual boot wasn't possible. I installed it, and now everytime I start my computer, I get the Grub Error 21. Now the only way I can get into Windows is if I boot from a recovery CD, and then boot into Windows. How can I fix this grub error, and get my computer back to just automatically starting Windows? Thanks so much!

---

### Post by bhaverkamp on 2010-01-26
Windows repair disk should be able to fix this. Make sure your USB Linux boot disk is disconnected when you do this. You should then be able to select the OS using the BIOS boot disk selection menus. As it is you have setup the boot disk to transfer to GRUB on your USB disk. Easy error to make.

---

### Post by efflandt on 2010-01-26
A common problem because Ubuntu installation does not tell you where it is installing grub.  So you accidentally installed grub to your main hard drive instead of to the external drive.  There is an **Advanced** button at the summary screen just before it begins actual installation of files that allows you to select where to install grub.

If you can still boot to the external drive when it is connected, you may want to first want to install grub on the mbr of that drive.  But exact instructions depend upon grub version.

To fix your main drive to regular Windows mbr, either web search "fixmbr" or following is one example of instructions [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

