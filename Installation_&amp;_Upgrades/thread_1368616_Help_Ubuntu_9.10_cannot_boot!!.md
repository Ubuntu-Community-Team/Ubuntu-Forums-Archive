---
title: "Help: Ubuntu 9.10 cannot boot!!"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by hopestorm on 2009-12-30
Hi ALl,
I had Ubuntu 9.10 installed with Windows 7 using WUBI.
It worked fine for a few weeks. Today I caanot boot into Ubuntu with the 2.6.31.16 kernel any more. The error message is: "Kernel panic - not syncing ....". however I can boot into kernel 2.6.31.14. I then changed the file /boot/grub/grub.cfg   to move the kernel 2.6.31.14 to the first.   After rebooting, once I choose "Ubuntu", the grub cannot start any more. Instead, a command prompt "grub >" is shown.

Right now I can still log into Windows but not Ubuntu. Is there a way to get back to the Ubuntu without out reinstalling? 


Many many tanks

---

### Post by Moozillaaa on 2009-12-30
Can you look in update history, and undo most recent updates?

---

### Post by hopestorm on 2009-12-30
The problem is that I cannot boot into the Ubuntu and there is no way to downgrade.

Thanks anyway

---

### Post by cyberbeast on 2010-01-10
This problem has already been fixed. Just load into 2.6.31-14 and update your system. It should boot into 2.6.31-16 properly! There have been issues with the latest 2.6.31-17 kernel module, so 2.6.31-16 problems have already been fixed.

I also experienced the same problems, but after the update, I was able to load both the kernel modules without any problems. 

NOTE: By update, I mean to perform an update AFTER the update that loads the new kernel. But if I am not wrong, the newer versions of the update does not require 2 separate updates. 

Good Luck! :)

---

### Post by MarioA on 2010-05-02
Look into this, it worked for me:
 [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

