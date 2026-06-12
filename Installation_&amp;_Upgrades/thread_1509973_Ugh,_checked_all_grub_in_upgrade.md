---
title: "Ugh, checked all grub in upgrade"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by bgmomof2 on 2010-06-14
I made a quick decision to upgrade to 10.04, and during the upgrade it wanted to upgrade the Grub.  I don't remember all the choices, but it asked where I wanted Grub installed and I checked all the boxes.  Yikes!  I messed up something.  Now the boot selection shows Windows XP, but when I select it the screen stays black and nothing.  So, where do I go to learn about Grub, where it's suppose to be installed, and where it's not, and how to uninstall?  I want to get into XP.  Thanks.

---

### Post by oldfred on 2010-06-14
See if this fixes it.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)


Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)
[https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1](https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1)

Then in Ubuntu run
sudo update-grub

---

