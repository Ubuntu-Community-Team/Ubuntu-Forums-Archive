---
title: "EasyBCD Grub problem"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by sbooder on 2008-06-24
Hi All,
         I have loaded Ubuntu 8.04 onto my Vista machine, and got as far as using EasyBCD to change the bootloader back to Vista. The only problem I have is now when I boot, I go to the Grubloader option that is under Vista and XP, hit enter and then am confronted with a curser and an option to hit tab.

How do I enter info into the grubloader entry in EasyBCD/Add/remove Entries/NeoGrub/configure, and the doc menu.lst.

I followed instruction to save the menu.lst from Ubuntu and storing it on the Vista drive to access for cut and paste into the menu.lst in EasyBCD, but the text I am meant to cut and paste is not in the original Ubuntu menu.list.

Please someone tell me what to enter to get this to work.

Thanks,
Simon.

---

### Post by sbooder on 2008-06-25
I solved it.

I removed the Grub loader from EasyBCD and added a Linux entry, called it Ubuntu, chose the appropriate partition and ticked the box Grub not in boot loader, and it now works.

The only thing that is untidy is when I choose Ubuntu from the boot menu and I then get the grub loader, it still has Vista as an option and of course I had that option on the previous page.  

I will have to take that out in Ubuntu menu.lst I suspects?

---

