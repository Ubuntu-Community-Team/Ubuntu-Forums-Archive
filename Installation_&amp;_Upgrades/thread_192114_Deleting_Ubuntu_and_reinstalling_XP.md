---
title: "Deleting Ubuntu and reinstalling XP"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by GPH on 2006-06-08
First, I just want to say that I still like Ubuntu and the purpose of this is to dual-boot Ubuntu with Windows XP.

Here's my problem:

I was running Ubuntu for a couple of weeks as my primary and only OS, but then decided that it would be nice to dual-boot XP with Ubuntu in order to play games. I booted my computer with Gparted Live CD and deleted all my partitions to make one big NTFS partition.

Now, when I boot my computer with my Win XP Install CD, it tells me that "Setup did not find any hard disk drives installed to your computer". When I boot without the CD, I get an Error 17 from GRUB....

What should I do to solve this problem ?

---

### Post by sherlock-holmes on 2006-06-08
[QUOTE=GPH]First, I just want to say that I still like Ubuntu and the purpose of this is to dual-boot Ubuntu with Windows XP.

Here's my problem:

I was running Ubuntu for a couple of weeks as my primary and only OS, but then decided that it would be nice to dual-boot XP with Ubuntu in order to play games. I booted my computer with Gparted Live CD and deleted all my partitions to make one big NTFS partition.

Now, when I boot my computer with my Win XP Install CD, it tells me that "Setup did not find any hard disk drives installed to your computer". When I boot without the CD, I get an Error 17 from GRUB....

What should I do to solve this problem ?[/QUOTE]
use ubuntu live cd and reinstall grub ....error-17 tell that it knows that there is a partition but it cannot recognise it...

---

### Post by GPH on 2006-06-08
Ok, thx.

But after that, what's the best way uninstall Ubuntu and install Win XP without getting that error ?

---

### Post by vasimakhtar on 2006-06-08
Hi,
I have same problem. I deleted winxp and installed Ubuntu on 80Gb harddisk, with no partition. So I want again to do dual boot with winxp. 
I can make partition with LiveCD and then delete ubuntu and and again install xp and ubuntu?
thanks.

---

### Post by mbgb14 on 2006-06-08
[QUOTE=sherlock-holmes]use ubuntu live cd and reinstall grub ....error-17 tell that it knows that there is a partition but it cannot recognise it...[/QUOTE]
How do you reinstall grub from the livecd?

---

### Post by wthanna on 2006-06-08
Here's what I would do. Boot from Windows XP installation CD. When it asks what to do with your partitions, remove them all, then create a partition to install windows to, leaving the rest of the disk (what you want to use for ubuntu) unpartitioned. Finish installing windows to the partition you created for it. When you are done, boot the Dapper LiveCD. Install Ubuntu, telling it to use the available free space. (leaving the Win partition alone). It should install and setup GRUB to allow you to choose your operating system when you boot.

---

### Post by mbgb14 on 2006-06-08
[QUOTE=wthanna]Here's what I would do. Boot from Windows XP installation CD. When it asks what to do with your partitions, remove them all, then create a partition to install windows to, leaving the rest of the disk (what you want to use for ubuntu) unpartitioned. Finish installing windows to the partition you created for it. When you are done, boot the Dapper LiveCD. Install Ubuntu, telling it to use the available free space. (leaving the Win partition alone). It should install and setup GRUB to allow you to choose your operating system when you boot.[/QUOTE]
Cool - but how does one install *just* grub if, say, your MBR is hosed, but the install is still intact?

---

### Post by wthanna on 2006-06-08
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

This is a link to the Wiki, describing how to recover GRUB

---

### Post by mbgb14 on 2006-06-08
Thanks alot, cheers!

---

