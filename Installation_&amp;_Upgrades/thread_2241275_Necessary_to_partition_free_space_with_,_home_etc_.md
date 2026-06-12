---
title: "Necessary to partition free space with /, /home etc when installing alongside win8?"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by zorgborg on 2014-08-25
I've built my own desktop and installed windows 8.1 from usb. I've tried installing 14.04 with usb (I know it boots the usb in EFI mode, as I can select 'EFI: *usb device name*' from BIOS), but it doesn't recognise any other OS's are installed, so of course I found I have to free up some space, and did this by shrinking NTFS (C:) in win8.

Looking at this guide [www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) it seems I have to manually partition the free space to have separate root, home and swap partitions before going ahead. 

I'm just wondering if I really need to do this partitioning, or if I can just select the free space and proceed without any formatting of it and ubuntu will automatically install fine anyway (and still be able to encrypt the home directory?).
 I'm guessing as the usb is being booted in EFI mode grub will be installed in the /efi partition already there?

If I do need to do the partitioning, formatting each as a logical partition seems best, but how big does the root partition really need to be, another guide says 20 GB is more than enough, but the one linked above uses 50 (50000 MB)?
Also, with fast boot enabled the usb drive with 14.04 on it boots fine, but I assume I should disable fast boot anyway?

Thanks!

---

### Post by Ksiencha on 2014-08-25
I'm not an expert in this, but I think you should totally have separate partitions for Ubuntu.
I myself created a dual-boot with Windows 7, you can see my partition table below. On my old laptop with much less HDD memory I used 20GB for **/** partition, here I have a lot of memory and I use 50GB for **/**. Again I'm not advanced in this, but all works decent, so I guess I did it right.

I hope this example table will help you ;)

---

### Post by kansasnoob on 2014-08-25
> I'm just wondering if I really need to do this partitioning, or if I can just select the free space and proceed without any formatting of it and ubuntu will automatically install fine anyway (and still be able to encrypt the home directory?).

I don't have new enough hardware to know anything about UEFI or such things, nor have I messed with Win 8 yet so I can't tell you what the best way is to partition for a dual-boot, but I can assure that it's NOT safe to depend on Ubuntu's automated installer options due to this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

So wait until you have a manual partitioning plan all figured out before proceeding.

---

### Post by grahammechanical on 2014-08-25
Perhaps you should read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The installer only creates a / partition where Ubuntu is installed and gives it a /home folder and a swap partition. To put /home in its own partition we need to create that partition and tell the installer that we want it to be our /home location. And to do that we need to use the Something Else option.

The advantage of having /home on it own partition is that if we need to re-install Ubuntu we can do so without losing our data or user configurations in /home.  I have separate partition for my data. So, I keep /home as a folder in the / partition. But I am in the situation of having to create another partition. You want to avoid that and that means that you have to accept the limitations of the installer.

When you run the installer and get to the screen that says Allocate Driver space, what options do you see? Do you get an option to install Alongside Windows? Just make sure that you do not select Erase the disk and install Ubuntu. That will remove Windows 8.1 and you will have to re-install it. 

Regards.

---

### Post by oldfred on 2014-08-25
Did you install Windows in UEFI boot mode? It probably will install in either mode and that depends totally on how you booted installer flash drive. 

Post this from terminal in live installer:
sudo parted -l

Do you have one drive or more than one?
Some advantages to having each system on its own drive.

---

### Post by zorgborg on 2014-08-25
Windows is installed in EFI mode yes. I had been looking at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and that's why I was wondering about if grub will recognise it's in EFI mode and use the EFI partition but I think this is probably a given now. I shouldn't have any secure boot issues as it's a custom install of win8.

Windows 8 isn't recognised, I don't mean go ahead with the 'use whole drive etc' option, rather once you had selected manual partitioning and selected free space then just clicked continue without partitioning. I'm gonna go ahead and make the partitions, seems the sensible thing to do :)

Btw, when using the stock windows disk management tool to shrink windows 8.1 C: drive, it may only shrink so far, even though there is clearly gazillions of free space, which can be to do with immovable files (yey), I got around this by using the free trial of PerfectDisk Pro to defrag, consolidate free space and optimise C:, along with following some tips in this guide [http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
After that it was able to shrink plenty more so I can dominate the HDD with ubuntu now :D

---

### Post by sotiris2 on 2014-08-25
Did you make sure that windows boot after you shrank their partition?

---

### Post by zorgborg on 2014-08-25
Yep, boots fine, but it should do seeing as I'm shrinking it with windows own disk management tool :)

---

### Post by zorgborg on 2014-08-26
Followed partitioning guidelines, ubuntu installed fine, grub game up after boot and shows windows boot manager in the entries, and after checking it did install in EFI mode too :)

---

### Post by Ksiencha on 2014-08-26
Wonderful! I'm glad that you got it to work :)

---

