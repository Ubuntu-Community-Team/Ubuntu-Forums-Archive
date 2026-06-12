---
title: "Dual boot question"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by callen41 on 2012-05-17
I'm dual booting with windows 7.  I have two hard drives.  Should I dual boot on the same hard drive as my windows 7 installation or the other one?  Does it even matter?

---

### Post by darkod on 2012-05-17
No, it doesn't. The choice is completely yours how you want to organize your system.

You can even have both OSs on the same hdd and leave the windows botloader on it, while installing grub2 bootloader on the other disk even though it doesn't contain the ubuntu OS. That way you can easily boot into windows directly by booting from the other disk.

For best control when doing the install, I always recommend the manual partitioning option (Something Else), it's up to you what you want to use.

---

### Post by fantab on 2012-05-17
> **callen41 said:**
> I'm dual booting with windows 7.  I have two hard drives.  Should I dual boot on the same hard drive as my windows 7 installation or the other one?  Does it even matter?

Like the post above says, it does not matter whether you install both OS on the same hard disk or on separate hard disks.

However, since you have an option of using two hard disks, I would suggest that you install them separately. Windows on one HDD and Ubuntu on one. That ways you can have Windows and its bootloader on one HDD and Ubuntu and its boot loader on another.

You will have to change the Hard Disk Boot order in BIOS to boot HDD with Ubuntu first. Ubuntu bootloader, GRUB will recognize Windows on the other Hdd and will give you an option to boot into it. 

Read and research about partitioning and about dual installations before you proceed. And plan in advance how you would like to partition your Hard Disks. Use [**GParted LiveCD**]("http://gparted.sourceforge.net/livecd.php") to partition your HDD.

---

