---
title: "GRUB Fatal Error Ubunto 14.04 LTS Install"
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by baudrillard on 2014-11-12
TL;DR ~75% through install, Ubuntu 14.04 throws a GRUB FATAL ERROR and quits installation on my primary laptop. Pls help.

Long story: I'm a Freshman CS major and I want to get into GNU/Linux based OSes for personal enjoyment/learning, and have managed to dual boot it on both of my laptops. I realized after having successfully installed Ubuntu on one PC that when I rebooted it, it skipped GRUB and went straight to W8.1. I checked the BIOS load, and it seems the PC deleted GRUB and now refuses to install because of GRUB failing to install every time I try to install. When it comes to Ubuntu I am still very new, so please treat me like a novice if possible. Details to follow:

Specs: Intel i7 4th generation processor, 16 gb RAM, 1 tb Hybrid Disk Drive w/ 24 SSD Cache, Nvidia GT750M SLI Graphics,** freshly installed Windows 8.1 Pro(literally 3 days ago),**64 bit system and OSes 

I have already attempted to re-install multiple times now, repeatedly reformatting the HDD partition that I use with Ubuntu clean from within Windows. Additionally, I used apt-get boot-repair from my live USB that I used to install Ubuntu on both of my laptops, but to no avail. While on that, that USB is not to blame because it installed perfectly fine on the laptop I'm using now.

Partition set up:

dev/sda 22.4 gb SSD - Cache
dev/sdb 1 mb - empty
dev/sdb2 ~150 mb - EFI Boot
dev/sdb3 ~200 - Windows Recovery
dev/sdb4 ~700 GB - Windows OS
dev/sdb5 ~140 GB - Empty, what was supposed to be Ubuntu (20 gb for /, 16 gb for Swap, and 100 gb for /home)

And I've always used the general 1 tb HDD option from the menu at the bottom of partition set up to boot from.

I'm sorry if any stats are not specific enough, I'm not currently at my other laptop, so I will gladly get specifics if needed. Thank you for any help!!!!!!!

---

### Post by yancek on 2014-11-12
Your output above shows that you have a separate EFI partition for windows.  That means you must install Ubuntu in EFI mode also or the result is what you get.  I don't use UEFI myself but from reading numerous posts here, there is some way you should be able to get that option booting the Ubuntu installation medium.  Take a look at the instructions at the Ubuntu page below for some help.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by baudrillard on 2014-11-12
I am 99.9% it is booting in EFI mode. I've already checked out that guide and I meet all the requirements of the first section, and when I boot from the USB, it takes me to that black screen(which the guide says indicates it's booting in EFI mode). Thank you, however.

Any other suggestions?

---

### Post by irv on 2014-11-12
Make sure you disable Secure Boot and Fast Boot in the BIOS. Before doing the Ubuntu Install.

---

### Post by baudrillard on 2014-11-12
I have indeed done this. Same goes for quick boot or whatever windows calls it. I also have intel rapid storage disabled(and eventually uninstalled to double check) as well.

---

### Post by yancek on 2014-11-12
If you have not done this, can you use your Ubuntu install medium and mount /dev/sdb2 to check to see if you have your Ubuntu efi files there?

---

### Post by grahammechanical on 2014-11-12
When we use the Something Else option we are given the option to tell the installer where to install Grub. It defaults to sda. But in your case sda is listed as cache. Could that be the reason the the installer is throwing up this error?

---

### Post by baudrillard on 2014-11-12
> **yancek said:**
> If you have not done this, can you use your Ubuntu install medium and mount /dev/sdb2 to check to see if you have your Ubuntu efi files there?

So are you suggesting for me to live boot on the USB and see if the GRUB launcher is on that partition still?

And even if so, what would I then do to go about and have Ubuntu know this and prevent a crash of the installer from the error?

If you know the terminal command, I'm willing to try it.

---

### Post by baudrillard on 2014-11-12
> **grahammechanical said:**
> When we use the Something Else option we are given the option to tell the installer where to install Grub. It defaults to sda. But in your case sda is listed as cache. Could that be the reason the the installer is throwing up this error?

I know what you're talking about. In that option, I'm able to choose from either A) Any of the dev/sda or dev/sdb partitions specifically or B)I'm able to choose the entire SSD Cache or the entire 1tb HDD.

On each installation, I've always chosen the 'entire' HDD drive, which is what I saw that was recommended by others. If you think I should switch up the boot directory, I'm up for it. I would like to have some assurance that there's a decent chance it would work/wouldn't wipe windows though. I honestly have nothing installed on Windows 8.1 right now because I just recently bought a new version and so I wouldn't be all that upset if it got wiped, but I would like to at least avoid it for now. I figure if this can't be solved, I could install Ubuntu first and then windows. But like I said, I want to avoid wiping windows un/intentionally for now.

A theory I have going right now is that on my HDD there's that partition of 1mb that is declared as 'empty' according to Ubuntu. On windows, it doesn't even register. I've looked it up and apparently GRUB is only like 512kb in size, so I'm wondering if that was where it was originally before it got wiped for some reason. Maybe boot there?

Alternatively, I've been told you can put GRUB in the same partition that window's EFI boot directory is, which sounds like it would solve the problem. At worse, I break the launcher for Windows which (i've read online at least) can be fixed by live booting Ubuntu and using boot-repair.

So yeah, I'm open to any suggestions! Just let me know.

---

### Post by yancek on 2014-11-12
> A theory I have going right now is that on my HDD there's that partition of 1mb that is declared as 'empty' according to Ubuntu

When you are using GPT partitioning and not using EFI, that 1MB partition is needed for Grub boot code.  If you have both windows and Ubuntu in EFI, you do not need it.  Your original output shows sdb2 as an EFI partition.  From what I have seen on various posts here dealing with EFI, both the windows and Ubuntu EFI files will go on this partition.  The fact that you have this EFI partition would indicate that windows 8 was installed EFI, so in order for Ubuntu to boot, you need to install it EFI also.  And yes, your previous post in response to my previous post, use the Ubuntu flash drive to mount sdb2 to see if the Ubuntu efi files are there.  I would not expect them to be.  I don't use UEFI so I'm not sure what you would need to do to repair this short of reinstalling but hopefully someone else will come along with a suggestion.

---

### Post by baudrillard on 2014-11-13
Alright, I'm having a bit of a busy week, so I'll start trying that this  weekend. I'll post an update then. Thank you all for the suggestions so  far!

---

### Post by oldfred on 2014-11-14
Is it a hybrid hard drive or a small SSD on motherboard that uses Intel SRT as Windows boot cache?

Some with larger cache SSD shut down cache and use that for / (root). Others turn off Intel SRT and install Ubuntu to hard drive and turn cache back on. Depends on whether primarily a Windows or Ubuntu user which you want a bit faster. You may have to remove RAID meta-data to get grub to install correctly.

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)


 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

