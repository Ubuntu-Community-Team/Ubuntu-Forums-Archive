---
title: "Windows 8 and Ubuntu double boot, but Ubuntu Installer doesn't see my partitions?"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by janethki on 2013-06-11
Hi, this is the first time I'm trying to double boot my computer with Ubuntu. I'm going to be using a lot of memory so I want to double boot rather than using a VM. I have Windows 8 pre-installed on my Dell Inspiron 14z so I know that there have been problems with that. I followed the steps and disabled Intel Smart Response Technology and Secure Boot. I feel like I have several problems that then come up that might be related to the Windows 8 thing or might not.

First of all, when I try to boot from my LiveUSB in UEFI mode, it comes to the GRUB menu with the correct options ("Try Ubuntu w/o Installing", "Install Ubuntu", etc.) but when I click anything, all I get is a black screen. I tried putting in nomodeset and deleting "quiet splash" but it didn't work. Booting from the LiveUSB in Legacy Mode, however, does work. So my thought process was that I could just install it in Legacy Mode, and then switch it to EFI mode later.

But, when I try to use the Ubuntu Installer, it doesn't seem to be able to see any of my partitions. The only thing I can select from the dropdown menu is dev/sda which is the correct partition, but in the main partition box thing, nothing shows up. I can't click any of the buttons either -- they're all greyed out. So I can't continue with the installation.

I shrank the windows partition to leave around 30 GB for the Ubuntu partition in Windows using Disk Management, but now I'm not too sure how to proceed. In [this]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system") answer, they do say to make the Ubuntu partition from within Windows. Is that what is preventing Ubuntu from being able to see any partitions? If so, how do you make a partition within Windows? Does this mean I need to make a swap partition and root partition using Disk Management?

[This]("http://askubuntu.com/questions/162631/ubuntu-12-04-installer-does-not-recognize-drive-partitions") thread also seemed to have a somewhat similar problem with the installer. One of the solutions seemed to be to run "sudo dmraid -rE" but that also seemed to do something to Nvidia RAID, which I think my Windows might use, although I'm not too sure what it is. If that is the problem, is there a way to run the command without damaging Windows?

I'm sorry if this was an incorrect thread or if this question has been asked already. I've been trying to do this for the past 4 days and have been reading these ubuntu forums, but I'm just not really sure how to proceed with this.

Thank you!

---

