---
title: "Install on USB hard drive no good"
date: 2006-04-16
forum: Installation &amp; Upgrades
---

### Post by doublem on 2006-04-16
Greetings,

Having heard so much about Ubuntu, I decided to install it to try it out. I have a mutli-boot system with two internal hard drives and a 200G external hard drive, which is connected through a USB port. My internal hard drives being mostly full, I decided to put Ubuntu in a partitiion on the 200G external drive. It installed OK, with the no boot loader option. Next I booted up in Mepis, from which grub was installed on the MBR, and added Ubuntu to the menu.lst, which is the list of OS's that tells grub what's available. Trying to boot Ubuntu gives an error. After fiddling around with the boot parameters, I finally realized that the USB ports aren't available at boot time, so grub can't see the external drive.

After much thought, I can't see a way around this problem. I realize that I could download a live CD, but trying to boot Ubuntu from the external drive has gone from a practical problem to one of principle, as well as a learning experience.

Can anyone offer any advice?

Thanks,
Mike

---

### Post by derjames on 2006-04-16
Hello there

please read the following thread by DABRUGO, it is quite useful and there you can find for sure a solution for your problem.

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

Hope this helps
Cheers

---

### Post by doublem on 2006-04-16
My apologies to all. I should have done a search first. I see this questions has been addressed many times.

My thanks to all who took the time to read my original post.

Mike

---

