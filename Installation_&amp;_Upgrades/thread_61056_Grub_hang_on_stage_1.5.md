---
title: "Grub hang on stage 1.5"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by Azmodan on 2005-08-30
I just installed Ubuntu on my sister's computer and when I rebooted, Grub hanged on stage 1.5.

The computer used to have Ubuntu installed without any problems but my sister wanted a dual-boot so I gave half of the hard disk to WinXP and re-installed Ubuntu on the second half.  It detected WinXP during the installation just fine.

I guess that I will have to use a LiveCD to solve the problem since the computer is now unusable otherwise but I don't know what to do.

---

### Post by weekend warrior on 2005-08-31
You *could* use a LiveCD to manually edit the grub files (menu.1st and/or grub.conf in /boot/grub/) but if you've just installed both OSes and have nothing invested you can just try again following the instructions here:

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

and all should be well. Or if you want to learn more about manual Grub editing [this link](http://www.gnu.org/software/grub/manual/grub.html#Configuration) will get you going.


Personally, if it's at all possible I would suggest one machine for XP and another for ubuntu, just to keep things nice and simple.  :) 


HTH

---

