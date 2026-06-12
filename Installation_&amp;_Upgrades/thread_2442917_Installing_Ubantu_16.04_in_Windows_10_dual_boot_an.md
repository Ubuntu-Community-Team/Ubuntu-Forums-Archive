---
title: "Installing Ubantu 16.04 in Windows 10 dual boot an error with EFI Boot partition"
date: 2020-05-09
forum: Installation &amp; Upgrades
---

### Post by subra26 on 2020-05-09
Hello support team,

While installing the Ubuntu16.04 from LiveUSB getting an error on the page "Something else"  below error

"The partition table format in use at your disks normally requires you to create a separate partition for boot loader code. This partition should be marked as on  "EFI Boot partition" and should be at least  35 MB in Size"

How to proceed from here.

---

### Post by Impavidus on 2020-05-09
If you install Ubuntu (or any other operating system) in UEFI mode, you need an EFI partition. With manual partitioning, you have to create that. It's a small FAT32 partition, usually near the start of the drive, marked as an EFI partition.

But you mention dual boot with Windows 10. If Windows 10 is already installed in UEFI mode, there must already be an EFI partition. If Windows 10 is installed in legacy mode (uncommon and not recommended), Ubuntu must be installed in legacy mode too and there won't be an EFI partition.

BTW, why Ubuntu 16.04? It has only eleven months of support left. Unless you have very specific needs, better install 20.04 or, if that's too new for you, 18.04.

---

### Post by yancek on 2020-05-09
The Ubuntu developers actually have a web site available explaining dual booting with windows 10 with a discussion of some of the problems you may encounter and solutions.  Start by reading through it.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by TheFu on 2020-05-09
+1 on not using 16.04 for a new install at this point.  We're still using 16.04 on most of our systems here, but we've had them running for 3+ yrs, in general.  Fall of 2018 was the last 16.04 physical box I brought up.

---

### Post by subra26 on 2020-05-11
Thanks for all your replies team.  actually i came to know from my friend that my laptop is SSD and for SSD the installation is giving problem for 16.04.. so I used now a old ACER laptop and managed to install Ubuntu successfully. Also, i need to use 16.04 version mainly due to our University project requirement need to develop in ROS - Kinetic for Robotic project.

---

### Post by TheFu on 2020-05-12
I use 16.04 on most of my systems still, including a laptop with an SSD.  2 prior laptops also had SSDs and ran some version of Ubuntu, so whatever you've been told has to be either incorrect or a very specific issue.

Some laptops don't implement the EFI standards correctly and need a little manual help.  Had a 2015 laptop from Toshiba like that. I just needed to copy over a few files to the non-standard place Toshiba wanted. Had a 2012 Acer that didn't have the issue.

For running older versions, we usually deploy those into either a VM or an LXD container, not as the base OS.  Don't lose the beachhead in the war against attackers.  Colleges have lots and lots of attackers.

---

