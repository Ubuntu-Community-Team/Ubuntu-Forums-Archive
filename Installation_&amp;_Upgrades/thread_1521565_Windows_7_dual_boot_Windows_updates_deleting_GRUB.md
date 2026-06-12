---
title: "Windows 7 dual boot: Windows updates deleting GRUB?"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Fillanzea on 2010-07-01
On 6/28 I set up my new computer, which came with Windows 7. I set it up as a dual boot system with Ubuntu 9.10, and it seemed to go fine. This is my first time setting up a dual boot system.

The next day, Windows automatically downloaded and installed a number of updates. The next time I tried to boot, it said that GRUB was not found and it couldn't find a hard drive to boot from. I couldn't boot into either Windows or Ubuntu. So I installed Ubuntu again on a new partition (I didn't want to write over the files in my existing Ubuntu partition). After that I was able to boot into Windows 7 or either of the existing Ubuntu partitions.

Today, again, Windows automatically downloaded and installed some updates, and the next time I tried to boot, it said a module did not exist and it couldn't find a hard drive to boot from. I am installing Ubuntu again.

Does anyone have any experience with this happening, and how I can stop it?

---

### Post by confused57 on 2010-07-01
Some computer manufacturers have "proprietary" software that tries to prevent changes to the mbr, such as Dell's DataSafe...here's someone in Linux Forums with the same problem as you're having:
[http://www.linuxforums.org/forum/ubuntu-help/162584-solved-win-7-ubuntu-dual-boot-grub-problem.html](http://www.linuxforums.org/forum/ubuntu-help/162584-solved-win-7-ubuntu-dual-boot-grub-problem.html)

I believe HP also may have a similar program.

---

### Post by Fillanzea on 2010-07-01
Thank you!

It is indeed a Dell with DataSafe.

---

