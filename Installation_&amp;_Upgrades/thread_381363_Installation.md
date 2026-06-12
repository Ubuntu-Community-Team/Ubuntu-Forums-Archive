---
title: "Installation"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by Flemming on 2007-03-10
I finally got Ubuntu installed using text mode.
The only thing is when getting to final screen when screen is asking to reboot and
remove disk close tray and ENTER.
When doing that nothing happens, it does not react to Enter?
I finally get sick of waiting and reboot the computer by shutting down and restart.
However, when starting Ubuntu I get the vertical lines again, so obviously it has not finalised the settings and giving me the vidio I have asked for.

Any idea all you smart people. i am new to this, but have heard so much good about Linus so thought I would try.
I get dual boot OK but neet to get into program to reset. Also my mouse doesn't seem to work, but maybe I can do that once the program finalize the install.

Please mail answer to [email]toveeve@optusnet.com.au[/email]
I seem to have to spend 20-30 minutes trying to find the answer to my question.

Thank you Flemming

---

### Post by zvacet on 2007-03-11
> Boot into Rescue Mode
First, find your trusty Ubuntu install CD and reboot your system to its initial boot screen. Among the number of options is "Recover a broken system." Select this option, and Ubuntu will start what appears at first to be the default installation program. You will be prompted for some standard language and network settings as you are during the installation, but these steps are only to set up the initial rescue environment. Notice that in the top-left corner of the screen, "Rescue mode" appears. 
Continue through these dialogs until you are prompted to choose your root device.
> If you installed Ubuntu in a dual-boot configuration with Windows, your root filesystem is probably the second partition in the list.
> This is a common symptom for an unbootable system. Perhaps you reinstalled Windows or some other operating system as a dual-boot system. Whatever the reason, your default GRUB boot menu is now missing and needs to be restored. 
From the rescue operations menu, select the "Reinstall GRUB boot loader" option. The next screen that appears is the same one you might remember being prompted with when you first installed Ubuntu. It asks you where you would like to install the GRUB boot loader. Unless you remember setting up GRUB somewhere in particular, chances are you probably installed it to the Master Boot Record on your first hard drive. If so, type (hd0) and then continue. The rescue mode will reinstall GRUB and drop you back to the main "Rescue operations" menu. Select "Reboot the system," and you should hopefully be presented with your standard boot menu. 

Post back if after this you still have problems.

---

### Post by wpshooter on 2007-03-11
Flemming:

What version of Ubuntu is it that you are attemping to install ?

Breezy, Dapper, Edgy or Feisty ?

---

