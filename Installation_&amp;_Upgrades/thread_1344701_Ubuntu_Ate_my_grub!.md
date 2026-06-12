---
title: "Ubuntu Ate my grub!"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by richardrosa on 2009-12-03
Greetings All, 

  I recently installed Ubuntu ver 9.1 on a multi-boot system, and it seems that a new level of GRUB has taken over.

 Originally, I booted /dev/sda1, which contained GRUB, and a number of other Bootable systems. Menu.lst on /dev/sda1 took care of ALL the OSs. One central location, one file to edit. 

 It looks like Ubuntu requires GRUB2, which also appears to require being installed in the MBR. I attempted to run 
   sudo grub-install /dev/sda3 
and GRUB2 complained that it MUST be installed in the MBR!

I do NOT want to have to boot Ubuntu just to update the boot menu, nor do I want that boot menu residing in the Ubuntu partition. 

I think I can restore my old MBR and return to my usual boot method.
However, is there a way to install GRUB2 onto the boot sector of the partition (rather than the MBR)? If not, will Ubuntu go nuts if I install the older GRUB? The plan would be to Chain Load to /dev/sda3 (the Ubuntu partition) from my original GRUB level.

 Thanx in advance.

  Rich

---

### Post by darkod on 2009-12-03
I think you can force it to install on partition with -f argument but if you are so happy with your other bootloader why don't you just keep it. In other words, tell grub not to install at all? But you already did the ubuntu install.

---

