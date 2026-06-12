---
title: "Problems loading after installing"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by Wldfire on 2007-05-08
Hello everyone. Total NEWBIE to Linux here. I downloaded the newest live CD, burned it and booted off it. I went through the menus and told it what to do, and installed. It installed nicely, but now when i reboot without the cd, i cant get it to load. I have three drives  2 IDE and a SATA. My Sata is my main drive that i boot off normally for Winblows. I installed it to my second IDE drive. 

I tried booting directly off that drive at startup with the motherboards boot menu, but it says it cant load it. Am i missing something? I really could use some advice on this as i really would like to give Linux a try.

I hope i have enough info, if not let me know and i will fill in the blanks missing.

Thank you.

Ken

---

### Post by bulldog on 2007-05-08
Hi,
Try to boot from the first IDE master hdd.
At the end of the install ubuntu install GRUB,and if you didn't change the install location,it should be installed on (hd0) by default.
This is usually the first master IDE hdd.

If you can boot ubuntu,we'll have to look at the menu.lst which is used by GRUB to boot your OS's.
Maybe we have to edit some lines to make the windows OS to boot.

---

