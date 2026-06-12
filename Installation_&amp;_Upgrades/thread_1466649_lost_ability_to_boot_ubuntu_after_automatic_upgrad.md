---
title: "lost ability to boot ubuntu after automatic upgrade."
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by mokelly1 on 2010-04-30
I have been using Wubi for a couple of months.  I was not aware it was just for testing.  I did a couple of automatic upgrades without any problem.  I did an upgrade yesterday which required a reboot and I lost my ability to boot to ubuntu.  

I come to the screen to choose between windows 7 and ubuntu.  I choose ubuntu and I come to a black screen that has a prompt, grub>

I followed several threads about restoring grub and found one that told how to mount root.disk so I was able to copy my home directory. I mounted it at /media/ub  I tried to restore grub by typing:
sudo grub-setup -d /media/ub/boot/grub -m /media/ub/boot/grub/device.map /dev/sda ... got a message "cannot stat grub boot.img".  It is apparently looking for boot.img in the /boot/grub directory.

I cannot find a copy of boot.img on any of my install or rescue cd's.

I would like to boot up the old Wubi to save everything before I install a new Ubuntu with its own partitions.

Thanks for your help.

---

### Post by kansasnoob on 2010-04-30
It sounds like you were bitten by this bug:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by mokelly1 on 2010-04-30
That worked. Thank you!

---

