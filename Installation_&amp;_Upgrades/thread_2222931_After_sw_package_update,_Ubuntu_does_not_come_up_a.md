---
title: "After sw package update, Ubuntu does not come up and I get to the grub page"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by EhsanMZ on 2014-05-08
Yesterday, I got the update notification and I installed everything. Then I restarted my system and now I'm not able to go to Ubuntu anymore, instead, I get to the GNU GRUB version 2.02 page.
I googled the issue but I could not find any fix yet. 

grub> ls 
(hd0) (hd0,msdos1) (hd1) (hd1,msdos1)

I have both Windows 7 and Ubuntu on my system.
Using live USB I did the following:
sudo mkdir /mnt
sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

But no success. When I mounted /dev/sda1 I noticed that I can see all the Windows files (like program directory in windows), but I don't see any of my files which  I had in my linux system. 
I've attached the boot repair file to this thread.

---

