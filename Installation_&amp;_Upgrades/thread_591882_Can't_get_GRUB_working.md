---
title: "Can't get GRUB working"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Mr_Threepwood on 2007-10-25
Hello, I've already posted a similar thread elsewhere but the problem never got resolved.  I've got a fairly tricky setup and I'm having a hard time getting grub working so that I can dual boot Ubuntu with Windows XP.

I recently wiped one of the hard drives, so now I have the one drive that has XP, and the other one has four partitions:

Ext3 with /
Swap
Fat 32
Unpartitioned (will be used for NTFS space later)

OK, so to add the the problem, all of my hard drives are SATA, and the one that has Windows XP on it is actually 2 hard drives in RAID0.

So during the Ubuntu install, it tried to put grub onto hd0, and I have no idea what that reffers to, since if I go to /boot there is no grub folder.  The numbers that are reffered to seem very misleading, does GRUB call hd0 something other than what the Ubuntu install does?

So at this point I figured I'd try online help files, and so far I've had no luck.  I've tried reinstalling grub by using " sudo grub-install hd0", but that fails saying "Could not find device for /boot: Not found or not a block device.".  I've also tried using the "find /boot/grub/stage1" in grub, and it claims that it's on hd(0,0).  But when I navigate to /boot there is no grub folder.

Another problem is I'm unsure about how Ubuntu/Grub deal with my raid drives, like if I'm accidently setting up grub to hd0, does that mean it's just one of the raid drives (which seems messed up), or does it take both?

Does anyone know what I should try?  I'd really like to be able to dual boot both XP/Ubuntu, but I'm having one hell of a time.

---

### Post by confused57 on 2007-10-26
You should be able to determine if Ubuntu recognizes your Raid as 2 separate drives by booting the live cd, opening a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a small "L"

Here's an excellent guide on grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

What happens when you try setting your bios to boot first to your Ubuntu drive?

---

### Post by Em-Buntu on 2007-10-26
Yes, you have to be careful with this or you can end up overwriting your Windows installation.
Grub's naming convention is different then Windows. Ubuntu will not see your Windows RAID configuration and see it as 1 or 2 disks. If you allow it to write to one, you will lose all your data on your RAID.
You can use the Gnome Partition Editor to make sense of your drive configuration and install Ubuntu accordingly.

---

