---
title: "Dual Boot Ubuntu with Windows 7"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by edmundac on 2011-12-26
Hello, I am interested in installing Ubuntu as a dual boot on my laptop. I currently have Windows 7 with a lot of programs I need already installed. Therefore, I need to install Ubuntu while keeping Windows 7 an all of my current data on my hard drive. I cannot risk losing my information so I need good advice about dual booting. Thanks

---

### Post by 2F4U on 2011-12-26
What exactly is your question? Your post seems a bit vague to me.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Mark Phelps on 2011-12-26
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by Frogs Hair on 2011-12-26
Here are two Wubi links if that is what you are interested in . Wubi is for trial use and not recommended for a long term installation .

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (Wubi Mega)

---

### Post by edmundac on 2011-12-26
Thanks Mark Phelps, I have four drives but one is used only to run .iso files through DAEMON Tools. I can remove it now but I will need it in the future to run the program, so do I still need to remove a different drive? Also, how much do I need to shrink the Windows 7 partition to run Ubuntu 11.10?

---

### Post by Mark Phelps on 2011-12-27
> **edmundac said:**
> Thanks Mark Phelps, I have four drives but one is used only to run .iso files through DAEMON Tools. I can remove it now but I will need it in the future to run the program, so do I still need to remove a different drive? 
If you want to install Ubuntu into its own partition, you will need to have no more than three partitions on the drive.  You can't add the partition back later -- as 4 primaries is a hard limit.

> Also, how much do I need to shrink the Windows 7 partition to run Ubuntu 11.10?
I generally use 30GB -- but that's because I don't want to run out of room down the road.

---

