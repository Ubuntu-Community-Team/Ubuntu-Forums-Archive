---
title: "GRUB loading error"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by jbisetto on 2010-04-15
I'm running a dual boot system, Windows7/Ubuntu 9.10. I wake up the other day and my monitor has the following message:

CD ROM Boot Priority ... no medium
GRUB loading
the symbol '???f?U??Sj*???' not found
Aborted. Press any key to exit

This was after putting the machine into sleep mode in W7. My guess is that the W7 update ran and corrupted the entries in the MBR table? Has anyone else experience anything similar?

---

### Post by oldfred on 2010-04-15
A variety of windows software seems to think it can use the MBR which is reserved for booting as a place to hide things.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

### Post by jbisetto on 2010-04-15
Thanks fred, I thought it might be the Dell Recovery. I'll look through the links you posted for more information.

---

### Post by jbisetto on 2010-04-15
I tried reinstalling grub but it didn't help, so I decided to just install fully blown Ubuntu. Goodbye W7 ;)

---

