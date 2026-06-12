---
title: "empty grub ?"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by gilnic on 2010-11-16
Hello, I downloaded and used usb to try ubuntu.I found I then cannot open Windows XP now.I read that you can change the start order in the grub file but when I typed in the terminal 
sudo gedit /boot/grub/menu.lst the grub file only has grubenv in it 1kb? Any thoughts on why this is so?
Gil

---

### Post by goinglinux on 2010-11-16
In later versions (9.10 and later) /boot/grub/menu.lst has been replaced by /boot/grub/grub.cfg. 

This link will help: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by drs305 on 2010-11-16
And for simply changing the timeout, default OS, etc, this link provides less detail than the community doc but will give you the info to make the changes:
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

Other links in my signature line may also be of interest if you want to learn more about Grub 2.

---

