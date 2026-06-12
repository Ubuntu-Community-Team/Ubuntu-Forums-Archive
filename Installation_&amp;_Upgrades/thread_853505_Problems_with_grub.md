---
title: "Problems with grub"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by vedran.omeragic on 2008-07-08
Hi,
I had my ubuntu installed for a long time, but on a irritating request of my brother, I was forced to install windows XP on my machine, alongside with ubuntu.
However, once I installed it, I was unable to start ubuntu again, system would automaticly start win.
After, I used my ubuntu cd, and using "rescue a broken system" I was able to install grub loader. 
Unfortunately, I've installed it in sda2, where windows is located, and now, I can't select windows XP in grub menu.
I was looking trough net, but was unable to find any solution to this problem...

Could some please help me?

---

### Post by upchucky on 2008-07-08
because of crappy world dominance attitude of windows, it must be installed first then ubuntu installed, your new win install rewrote the master boot record of your drive, and cause it does not play fair it will not let ubuntu boot.

get supergrub, it will fix grubloader, and windows mbr also. there is a version of supergrub that has advanced features, that is the one you want.

if supergrub can load both or either os then with a bit of reading you will be able to fix instead of a reinstall.

knoppix live cd is great for fixing broken windows, and editing ubuntu files if neither os will boot

---

### Post by VMC on 2008-07-08
I don't think people learn much using Super Grub. Here is a document that restores Grub after Windows wipes it out:
[http://onlyubuntu.blogspot.com/2008/06/howto-re-install-grub-after-windows.html](http://onlyubuntu.blogspot.com/2008/06/howto-re-install-grub-after-windows.html)

---

### Post by stchman on 2008-07-08
> **vedran.omeragic said:**
> Hi,
I had my ubuntu installed for a long time, but on a irritating request of my brother, I was forced to install windows XP on my machine, alongside with ubuntu.
However, once I installed it, I was unable to start ubuntu again, system would automaticly start win.
After, I used my ubuntu cd, and using "rescue a broken system" I was able to install grub loader. 
Unfortunately, I've installed it in sda2, where windows is located, and now, I can't select windows XP in grub menu.
I was looking trough net, but was unable to find any solution to this problem...

Could some please help me?

XP erases GRUB from the MBR.  You need to reinstall GRUB.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Tell your brother to get his own computer.

---

### Post by vedran.omeragic on 2008-07-09
> **VMC said:**
> I don't think people learn much using Super Grub. Here is a document that restores Grub after Windows wipes it out:
[http://onlyubuntu.blogspot.com/2008/06/howto-re-install-grub-after-windows.html](http://onlyubuntu.blogspot.com/2008/06/howto-re-install-grub-after-windows.html)

Thank you, it worked perfectly and now I can access XP from grub menu.

> **stchman said:**
> Tell your brother to get his own computer.

Well, technincly that is his comp, though we bought it together but I don't use it unless I'm home, which is only a week per 3/4 months.
And the worst part is, he wants XP only for games. I've tried bribing him with cedega, but it didn't work :)

---

