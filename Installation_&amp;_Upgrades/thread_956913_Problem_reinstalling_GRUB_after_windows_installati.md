---
title: "Problem reinstalling GRUB after windows installation"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by Flicules on 2008-10-23
I have just recently reinstalled my Windows...so it changed the MBR so no GRUB, so i can't boot my Ubuntu
I've read some of the posts but they don't seem to work.The trouble is my 2 WD are in RAID.I've tried to recover GRUB the way it sais here [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) and it does not work.

I booted my live CD(8.04) and installed dmraid drivers..

I used the following as in the post:

sudo grub
grub>find /boot/grub/stage1

After this...it sais File not found.
How can i install GRUB?pls help guys.

---

### Post by Dr Small on 2008-10-23
> **Flicules said:**
> I have just recently reinstalled my Windows...so it changed the MBR so no GRUB, so i can't boot my Ubuntu
I've read some of the posts but they don't seem to work.The trouble is my 2 WD are in RAID.I've tried to recover GRUB the way it sais here [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) and it does not work.

I booted my live CD(8.04) and installed dmraid drivers..

I used the following as in the post:

sudo grub
grub>find /boot/grub/stage1

After this...it sais File not found.
How can i install GRUB?pls help guys.
Please read this thread:
[http://ubuntuforums.org/showthread.php?t=950820&highlight=SuperGrub](http://ubuntuforums.org/showthread.php?t=950820&highlight=SuperGrub)

---

