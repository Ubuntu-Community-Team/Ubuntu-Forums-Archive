---
title: "How to install Grub without messing MBR?"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by Jored on 2007-12-09
My upgrade from 7.04 to 7.10 froze about half way and destroyed the original 7.04 system. 

I am now ready to reinstall from a LiveCD.

I do not want to have Grub install in the MBR. 

There is a very long thread, going back to 2005 but still open and active with lots of up to date posts, which clearly explains how to install Grub in a floppy or USB pendrive and then transfer some of the boot parameters to boot.ini in Windows to enable dual boot without having Grub in the MBR.

No way I can find it. Any help?

---

### Post by jjross on 2007-12-09
See if this link is the one you are looking for
[http://ubuntuforums.org/showthread.php?t=56723]("http://ubuntuforums.org/showthread.php?t=56723")

Edit, this does work, i used it a few years ago until I became comfortable with GRUB

---

### Post by logos34 on 2007-12-09
The easiest way is [Wingrub]("http://users.bigpond.net.au/hermanzone/p9.html").

Or use this guide:

[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)

Or just use the flopoy to boot.  Enter '(fd0)' in place of '(hd0)' on the bootloader screen (-->page 7 'Ready to install' screen>hit 'Advanced' button lower right)

---

### Post by Jored on 2007-12-12
Thank you. I´ll be working late tonight  . . .

---

### Post by maybeway36 on 2007-12-12
You could install GRUB to Ubuntu's partition.
The floppy disk boot method is also good for dual-booting multiple Linux distros.

---

