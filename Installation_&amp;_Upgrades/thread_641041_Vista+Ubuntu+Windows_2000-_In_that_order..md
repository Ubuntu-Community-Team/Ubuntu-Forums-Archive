---
title: "Vista+Ubuntu+Windows 2000- In that order."
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by GeigerRulesBig on 2007-12-14
II purchased an Acer Apire 5570Z last summer. It came pre-installed with Vista, but I soon grew frustrated and set it up to dual-boot Vista/Ubuntu (Then Feisty, now Gutsy) 

I want to set it up to also boot Windows 2000, but I do not want to redo my Vista or Ubuntu installs. I have dual booted 2K and 98 before, and I know it is always hard to get a dual boot setup without having the various Windows versions overwrite their main system files. Does anyone have an idea on how I could go about this without screwing over my Vista or Ubuntu installs, and have it all boot from the GRUB panel?

Thanks in advance.


-Geiger

---

### Post by ectospasm on 2007-12-14
This is pure conjecture, since I've never done what you describe, but I think it would be as simple as installing W2K on that tertiary HDD, letting it step on your MBR, and then reinstalling GRUB.  I would backup your grub.conf (and/or menu.lst), and proceed that way.  I guess the trick would be to keep W2K from stepping on either Vista or Ubuntu, which may be the most difficult thing of all to do, and is completely outside my expertise...

I would backup anything and everything you don't want to lose on this system, and be prepared to do a complete reinstall of everything should W2K puke on it.  Unfortunately Microsoft has never been one to play nicely, even with its own children.

Good luck!

---

### Post by Herman on 2007-12-15
You should be able to make use of GRUB's 'hide' and 'unhide' commands.

First you use GRUB's 'hide' command to hide your Windows Vista so that your Windows 2000 that you are going to install won't 'see' it and set up a Windows default style dual boot.
Nobody would want a Windows default style dual boot because that means important system files from the operating you are installing will be copied to the existing operating system, making that your 'boot partition'. That means one operating system will be dependent on the other, so if you lose Vista for some reason, (like a virus maybe), you lose the boot of both operating systems.
[    Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm") Dan Goodell

Then when you have Windows 2000 installed you'll need to re-install GRUB, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") eg; with Live CD.

Finally, you'll want to edit your /boot/grub/menu.lst file in Ubuntu to hide and unhide either Windows from the other and  boot whichever one you select, 
[More than one Windows on the same disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk")  ...use hide and unhide commands.

You can also do the same thing with [GAG Boot Manager]("http://gag.sourceforge.net/") from a Graphical environment (instead of needing to learn terminal commands, you can select what you want to do from menus with GAG),  [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

Many other boot managers can 'hide' and 'unhide' Windows partitions too. 
  
Regards, Herman :)

---

### Post by GeigerRulesBig on 2007-12-15
Thank you for your responses. If everyone else has any suggestions or tips, feel free to chime in. I will post the results.


-Geiger

---

