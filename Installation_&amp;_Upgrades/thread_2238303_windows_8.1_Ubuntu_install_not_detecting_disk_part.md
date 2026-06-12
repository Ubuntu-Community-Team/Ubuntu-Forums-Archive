---
title: "windows 8.1 Ubuntu install not detecting disk partitions"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by tom128 on 2014-08-07
Hi 

I have a windows 8.1 laptop. I created a partition on my hard drive and burnt and Ubuntu CD (64bit) to install into the partition. 

The install starts OK when booted from CD, I successfully choose a language and wireless network etc. However when it comes to the installation type to select the device for boot loader installation (where you are supposed to select the disk partition) however this table is blank. And drop down at bottom just says /dev/sda and nothing else. How do I see my hard disk?? 
If I click on the +- or change buttons it appears to freeze the install. 

Any ideas? Slightly frustrating... I tried shrinking my main C drive an leaving the space unassigned. I then tried making it a new empty windows drive, same results. Safe and fast restart is turned off.

---

### Post by mastablasta on 2014-08-07
/dev/sda     means **d**evice **s**csi **d**isk **a** 

it might be better to boot into the Ubuntu OS first then run the boot info summary found in boot repair tool: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

you will get a link and paste that here.

why you can't see windows can be for various reasons. scritp should tell us how the disk is setup. another option is to go into windows disk manager and make a screenshot there and then post that here.

---

### Post by tom128 on 2014-08-08
Here is the disk partition manager in windows. The only one I have created is the unallocated space by shrinking the main C drive.

I'll try the boot info summary tonight.

EDIT: here it is [http://paste.ubuntu.com/7986704/](http://paste.ubuntu.com/7986704/)

---

### Post by tom128 on 2014-08-08
I had a quick look at the link and although it's new to me I spotted something about using GNU parted - so ran this which fixed the partition issues for me.

Mate thanks for the link to that boot summary. Will carry on with install and if successful will solve this up.

Cheers

---

### Post by oldfred on 2014-08-08
You have an Ultrabook with Intel SRT for fast startup in Windows. Many have posted that with your 32GB SSd mSATA drive the SRT only uses a small part of it.
Some erase the RAID and stop using SRT and install Ubuntu / (root)  into the SSD with /home on hard drive. Other only use part of it for root. And some just install / & /home to hard drive and re-enable SRT.
The Intel SRT is seen as RAID and Ubuntu used to not see the RAID at all. Now it seems to see it, but grub2 from desktop installer will not install to RAID correctly. And with SRT you do not want grub installed into the RAID, but just into the efi partition.

Some are older installs & 14.04 does work better now. And Intel SRT is essential the same from all vendors.
       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

