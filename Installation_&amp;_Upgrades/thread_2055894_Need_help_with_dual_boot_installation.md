---
title: "Need help with dual boot installation"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by Radamand on 2012-09-10
I have a new computer with a blank HD.
My old computer has a nice SSD with my Ubuntu 12.04 system on it. 
I want to put my SSD into the new machine as the primary drive, THEN I want to install Win7 on the blank HD (NTFS), and set them up to dual boot.

Is this feasible? or do I need to reinstall Ubuntu and start from scratch?

If it's possible, can someone give me some pointers on things i would need to configure, and/or a tutorial? I'm guessing I need to re-config my grub to see both drives/OSs but i'm not sure how to do that.

I found a couple of tuts but nothing that quite matches my situation... I'm fairly proficient with Linux, but this is a bit out of the norm for me.

---

### Post by oldfred on 2012-09-10
I would install Windows to HD. If you do not want Windows to use entire drive then create a NTFS partition to install to. It has to be a primary partition with the boot flag formated NTFS. If you create one in advance it will also install to just that one. I also prefer to have a smaller system partition of 30 to 50GB for Windows and use another NTFS partition for shared data. Then from Ubuntu you do not have to write into the Windows system partition. 

A normal install of Windows 7 is a hidden boot/repair 100MB partition so you can encrypt the main partition. Or it may help in being able to boot repair partition and fix main install. But you can easily create a repairCD or USB for those emergencies.

Then just plug in the SSD, keep Windows as sda. Set BIOS to boot the SSD. Ubuntu will not really care that it is not the same drive number as it uses UUID. The only other issue may be if you have installed proprietary drivers for video. If so uninstall those first. If new system needs nVidia then you will have to use nomodeset on first boot.

Once booted run this and it should find the Windows install and add it to the grub menu.

sudo update-grub

---

