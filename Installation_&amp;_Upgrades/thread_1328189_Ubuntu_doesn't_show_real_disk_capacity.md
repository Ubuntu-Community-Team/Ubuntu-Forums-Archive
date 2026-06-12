---
title: "Ubuntu doesn't show real disk capacity"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by Brian88 on 2009-11-16
I have already installed Ubuntu on an 8GB Kingston Flash drive.
I reserved maximum extra space (6.8GB).

But in the home folder and in the / (root folder) it only shows as 68.9 MB free. Firefox won't work (it says insufficient drive space for security needs). I installed Opera, then the drive's freespace getting down to 28.7 MB. The persist feature works (all the changes is preserved in the next boot).

How can I claim my full 6.8GB free space?

Thanks for all your help.

---

### Post by darkod on 2009-11-16
You need to clarify first, you INSTALLED Ubuntu to the usb stick or you just created a 8GB usb startup stick with Ubuntu on it?
I am asking because I think the question to reserve space was when creating startup usb stick. When you are installing there is no such question (not that I have noticed), you just create partitions and install. In that situation all 8GB should be available to you (or 6.8GB).

---

### Post by Brian88 on 2009-11-17
Yes, I am creating an USB startup disk (System > Administration > Create a USB Startup Disk).

---

### Post by Mighty_Joe on 2009-11-17
> **Brian88 said:**
> 
How can I claim my full 6.8GB free space?


I don't think you can.  The maximum file size on a FAT32 filesystem is 4GB.  The "freespace", actually a persistent file named casper-rw, is implemented as one big file.

---

### Post by darkod on 2009-11-17
Not that I am trying to change your mind but why would you like to install software/packages on a startup disk?
That usb stick will be for trying ubuntu or installing ubuntu on computers. Once it's installed properly you can add as many pckages as you like and have free space as much as the hdd will allow you.

PS. I would understand if you want to install it on the stick, you will not have much spare space but it would run. If you setup grub2 to install on the stick you could then boot your ubuntu on any computer allowing usb boot and work on it. All files you create will be on your stick and you could use it anywhere. Is that what you are trying to do?

Because adding packages to the startup usb stick does not make any sense. Startup disks are only to try or install. It is different matter if you want to run ubuntu from a usb hdd/stick.

---

### Post by Brian88 on 2009-11-18
> **Mighty_Joe said:**
> I don't think you can.  The maximum file size on a FAT32 filesystem is 4GB.  The "freespace", actually a persistent file named casper-rw, is implemented as one big file.

So I can't have the 6.8GB 'freespace' (persistent file) then?

[QUOTE darkod]Re: Ubuntu doesn't show real disk capacity
Not that I am trying to change your mind but why would you like to install software/packages on a startup disk?
That usb stick will be for trying ubuntu or installing ubuntu on computers. Once it's installed properly you can add as many pckages as you like and have free space as much as the hdd will allow you.

PS. I would understand if you want to install it on the stick, you will not have much spare space but it would run. If you setup grub2 to install on the stick you could then boot your ubuntu on any computer allowing usb boot and work on it. All files you create will be on your stick and you could use it anywhere. Is that what you are trying to do?

Because adding packages to the startup usb stick does not make any sense. Startup disks are only to try or install. It is different matter if you want to run ubuntu from a usb hdd/stick.[/QUOTE]

If I am installing it on the disk, how many GBs of free space will I get? (My flashdrive is 8GB).

Beside that, will this trick ([http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/")) work? Because some of my computers are older (early Pentium 4), so it needs that CD to boot Ubuntu from USB. Will it work?

Thanks...

---

### Post by darkod on 2009-11-18
Well, in theory you could use all of the space, which is 7.5GB for 8GB usb stick due to the difference between billion Bytes and 1GB. You could have swap partition set at 1GB because of the limited space, so the rest for / would be 6.5GB all usable. Grub would have to be installed on the stick though, or if you find alternative way of booting it.
As for whether it will boot on older computers, sorry but I don't have much experience with that. I wouldn't like to misguide you. :)
You could always try, and you learn new things that way.

---

### Post by Brian88 on 2009-11-18
Thanks for all your help. 

After reading some articles and Wikipedia, and Mighty_Joe's post, I realized that the maximum filesize is 4GB. 

The solution: I formatted my flashdrive, and partitioned it into two : a 4.6GB for Ubuntu and the rest (3GB) for data. I put the Ubuntu USB startup install in the 4.6GB partition with 3.9GB persistent file.

The installing takes 2 hours to complete (as I only have the fullspeed 12MBit/s USB port), but as the result I got 3.5GB of free space! 


Thanks for all your help. It is now marked as solved.

---

