---
title: "What happens to GRUB when you format and re-install a Linux partition?"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by lefen on 2007-05-08
Hay all,

I'm considering upgrading from Dapper to Feisty. At the moment I'm dual booting Dapper with Windows XP. 

Assuming I wanted to upgarde by formatting my Linux partition and then start over with the Feisty live CD for installation - what would happen to GRUB? Would the Feisty live CD take care of everything (by reinstalling GRUB and configuring it), or would the installed version of GRUB I currently have autodetect the change following the fresh install?

BTW, I'm sure there are much easier ways of upgrading, but I'm gonna have to learn about this at some point I think ;)

Thanks for any help.

---

### Post by heimo on 2007-05-08
Parts of the grub lives on your Dapper partition. Formatting the partition will kill grub, you won't be able to boot using it before you've reinstalled some bootloader. Feisty install should be able to create new grub, and even add your Windows XP as boot option automatically. At least it will boot to new Feisty install and you can fix grub configuration from there if needed.

Fresh install may be wise option, but if you have time and want to learn, you could try to use "online" upgrade from Dapper to Edgy and then from Edgy to Feisty. If that fails - or you just want a "new start", you can always make a fresh install afterwards. Be sure to backup any valuable files before any major upgrades and changes to partitions.

---

### Post by phiphedog on 2007-05-08
I have the same setup as you and did the upgrade a few weeks ago. I just put in the feisty cd and booted from it, then double clicked the install and when it rebooted grub had the new feisty and XP to choose from. I believe the grub looks for the /boot/grub/menu.lst file to list the operating systems/kernels to boot.

So to answer your questions the Feisty live CD will take care of everything (by reinstalling GRUB and configuring it)

---

### Post by lefen on 2007-05-08
Thanks for the quick responses, I'll give this a try (^-^)

---

