---
title: "Grub issues"
date: 2014-10-22
forum: Installation &amp; Upgrades
---

### Post by Kevin_Purcell on 2014-10-22
When I installed Ubuntu 14.04 to my system, it installed a GRUB boot menu, all was well and good for the first boot, after which; each time I boot my system, it shows be a terminal based version of grub, and won't like me boot in to my Ubuntu installation. After I type exit, it exits GRUB and shows me a boot menu with the selections of drives to boot to. I select the hard-drive with both windows and Ubuntu installed but I get 3 Options:

- Ubuntu
- Windows Boot Manager
- ubuntu

Neither versions of Ubuntu work, but Windows does.

If anyone has any ways of removing this type of GRUB it would be helpful, I have tried using the methods of using the windows install discs command prompt and running the commands there, but that also did not work.

Thanks,
Kevin.

---

### Post by Bucky Ball on 2014-10-22
Welcome. If you could tell us what is actually happening when you choose Ubuntu. Are you getting an error message? If so, what? A black screen?

If we can get into Ubuntu will make it easier to see what is going on. Installing another boot manager to fix Ubuntu not booting is probably not going to work and may just complicate the issue.

How are you booting Windows? Is it on the grub menu with Ubuntu after you type 'exit'?

---

### Post by fantab on 2014-10-22
Boot from Live Ubuntu dvd/usb... Try Ubuntu without installing.
Download and install [Boot-repair]("https://help.ubuntu.com/community/Boot-Repair") tool.
Run the option 'Create Bootinfo Summary' in Boot-Repair, note down the url link it creates to the bootinfo file and post it back here. (Don't run the 'repair' option at this stage, lets see the bootinfo first).

---

