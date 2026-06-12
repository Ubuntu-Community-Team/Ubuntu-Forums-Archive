---
title: "Ubuntu won't boot after installation?"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by SuperSnake2012 on 2007-06-03
I'm trying to install Ubuntu 7.04 on my machine right now... I'm using an AMD Athlon 64 3000+, 2gb of RAM, ASRock dual-939 mobo.I have two hard drives, one is SATA and the other is IDE. I installed Ubuntu on a SATA HD. I booted Ubuntu from the CD and installed it through the LiveCD. I formatted my SATA drive completely so I would not have Windows XP on. The installation seemed to go well... it installed completely, and the Ubuntu installer told me to restart my computer and remove the disk. After the computer posts, I just get an error saying "Error loading operating system". I have no idea what's wrong... can anyone help? I'm posting from the LiveCD right now and I have no OS on here :(

---

### Post by confused57 on 2007-06-03
It's possible that grub's IPL was installed to the mbr of the IDE drive...you might want to go into bios & set your IDE drive to boot before the SATA drive.

---

### Post by SuperSnake2012 on 2007-06-03
Great call confused! I set my IDE drive as my first to boot and the boot loader came up and Ubuntu works now. I feel stupid after trying to get this to work all day! :p Thanks a lot :D

---

### Post by confused57 on 2007-06-03
> **SuperSnake2012 said:**
> Great call confused! I set my IDE drive as my first to boot and the boot loader came up and Ubuntu works now. I feel stupid after trying to get this to work all day! :p Thanks a lot :D

I thought that might be the problem...if you ever need to remove your IDE drive, grub's IPL can be installed to your SATA drive mbr, using the live cd...you'd need to make a few adjustments in your /boot/grub/menu.lst, i.e. root would need to be (hd0,x), instead of (hd1,x)....glad it worked..

Added:  In fact, it "shouldn't" hurt anything to go ahead and install grub to your SATA drive mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
"find /boot/grub/stage1" should result in "root (hd1,x)"...your would select "setup (hd1)"

then to test if it worked, set your SATA drive to boot before your IDE drive, you should get a grub boot menu, highlight your Ubuntu entry, press "e", change root from (hd1,x) to (hd0,x), then press "b" to boot...this change is temporary, so it won't affect your current setup and let you know this would work.
You might want to leave your system setup as you have it...boot IDE, then SATA...then if you ever need to boot from your SATA drive, you can follow the above procedure(you wouldn't need to dig out the live cd)...just an idea.

---

