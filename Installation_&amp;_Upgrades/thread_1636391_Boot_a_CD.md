---
title: "Boot a CD"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by dragonwrenn on 2010-12-03
Hi

I bought a Macbook Pro today, and installed Ubuntu alongside OSX.  My mistake, the GRUB has now prevented the OSX from loading at all.  Also, I can't boot a recovery CD for OSX nor can I get to the EFI (the command-option-f-o thing isn't doing anything).  I downloaded efibootmgr, but typing in sudo modprove evifars still has it produce the same error of "Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root."

Thus, I cannot boot OSX, I can't boot OSX's recovery CD.  This is a huge problem, really need help
Also, I installed Ubuntu from a live CD and didn't even see anything to chose not to install the GRUB.


Thanks!

Edit:
Here's the error message when I boot OSX from GRUB:

(the final segment before it loops)

USBMSC Identifier (non-unique): 000000009833 0x5ac 0x8403 0x9833
Still waiting for root device <--- loops here

---

### Post by zvacet on 2010-12-03
See if [http://ubuntuforums.org/showthread.php?t=1405867&highlight=add+osx+grub](http://ubuntuforums.org/showthread.php?t=1405867&highlight=add+osx+grub) can be of any help to you.

---

