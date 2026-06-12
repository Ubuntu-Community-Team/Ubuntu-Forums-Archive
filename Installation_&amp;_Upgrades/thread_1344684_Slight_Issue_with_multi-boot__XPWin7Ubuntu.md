---
title: "Slight Issue with multi-boot:  XP/Win7/Ubuntu"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by nuccx2001 on 2009-12-03
Slight issue Multi-booting 

I installed in the following order.

XP 
Win7
Ubuntu 9.10

Everything seems to be working.  But here is what I want to do.

I want to make Win7 the default OS. (dont hate me)

When I boot, I get the Grub loader, which has Ubuntu and Win 7 listed

If I boot win7, XP is also listed.  Perfect.

Problem is:  I cant find menu.lst

it's not in /boot/grub.

Any thoughts?

---

### Post by darkod on 2009-12-03
9.10 comes with Grub2 which does not use menu.lst like grub1. The editing is done in different way. Here are basics:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Actually the setting about the default OS is in /etc/default/grub. What you want to do is count the place of Win7 loader in grub menu, it will be 5th for example, or 7th. Depending how many kernel you have showing.

Then open:
sudo gedit /etc/default/grub

And change the Default number accordingly. I guess you know it need to be one less, for 5th in the menu put 4. After you have saved and closed the file run
sudo update-grub

---

### Post by nuccx2001 on 2009-12-03
Solved...  Worked like a charm!

Thanks a bunch.

---

