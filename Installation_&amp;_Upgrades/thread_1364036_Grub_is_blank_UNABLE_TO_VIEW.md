---
title: "Grub is blank: UNABLE TO VIEW"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by axelhdz2k3 on 2009-12-25
I just installed Ubuntu 9.10 and I am trying to dual boot XP. I have done this in the past with Ubuntu 9.04 and XP. My problem is I cannot see the GRUB. I type sudo gedit /boot/grub/menu.lst and the GRUB window opens but it is blank.

Thanks

---

### Post by oldfred on 2009-12-26
If you did a new install of Ubuntu 9.10, you now have grub2(1.97betaa4). Grub2 does not use menu.lst but has grub.cfg which you are not supposed to edit.
If you need to update it for a missing entry:
sudo update-grub

Other info:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

