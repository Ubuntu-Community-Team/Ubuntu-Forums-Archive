---
title: "Wiped out Windows bootloader"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by killercal on 2012-04-27
Hello,
 
I'm running Ubuntu from an exteranal USB HD. My reason for doing this is so I can carry my personal computer (USB HD) with me on my work trips and just use my work laptop as the hardware.
 
So I was upgrading Ubuntu 12.04 through the terminal and was prompted to install a GRUB because it couldn't find it on all drives. I selected the windows drive by accident and it removed the bootloader so I can't load windows unless I boot it from the GRUB on my HD. My question is; can I fix/repair/replace my WindowsXP bootloader on my work laptop without having the CD?

---

### Post by oldfred on 2012-04-28
You can manually reinstall grub2's boot loader to the external, install Windows or a Windows workalike to the internal, but grub also remember where to reinstall on updates, so you should update that also.

This goes thru all the process.

Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

Or you can do parts manually:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

