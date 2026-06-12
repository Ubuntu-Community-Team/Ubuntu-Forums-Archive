---
title: "Multiboot from Hardware Token"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by thelownage on 2011-05-05
I'm sure there has to be a post around here somewhere with what I'm looking for, but I still can't see it. I've tried switching up the search terms, but still nothing. I've found threads about installing the entire operating system on a flash drive, and I've done. What I'm trying to do now is to set it up so that multiple operating systems are installed on a partitioned hard drive, but that the system will not boot without USB device inserted. More specifically the setup is like this:

+500 GB Hard Drive
-+50 GB Extended Partition
--+10 GB Logical Partition
--+10 GB Logical Partition
--+10 GB Logical Partition
--+10 GB Logical Partition
--+10 GB Logical Partition
-+4 GB Swap Partition
+Remaining Partition mounted at /home/<username>/Shared (so I can access important docs from any OS)

I intend for the first 3 logical partitions to be permanent, with the second 2 for experimenting/ playing with. I've played around enough that mounting, partitioning, and editing the menu.lst file are no big deal. Would I just tell every instalation to put /boot on the USB device? If so should each install overwrite the old one on the USB, or partition the USB and chainload GRUB off each partion from it's first partition's menu.lst?

Any ideas or links to threads, walkthroughs, etc that would be relevant are appreciated. As I said I'm sure it's been done, I just can't find it.

---

### Post by Dutch70 on 2011-05-05
I would think that you can just choose to install the boot loader to your usb stick with every install. I see no reason why that wouldn't work. It would be just like another hdd.

Also, it's not a good idea to share a separate /home partition. The best way to multiboot is keep /home in with /, and share a data partition. Then you can symlink the folders you create in your data prtn to /home of each install by middle clicking & dragging them to your home directory.

Mind if I ask why in the world would you want your computer to not boot without a usb stick? 
You may want to use a few different usb sticks with a bootloader on each, since it will be like a key to your computer.

Secondly, you may need 2 usb sticks anyway unless you're using a cd to install. You may not be able to install the bootloader to the live usb your using for install.

---

### Post by thelownage on 2011-05-05
That would be the obvious choice. (My head is caught up on my finals next week and the impending vacation) I'll confirm when I'm done torrenting the ISOs. I have a slow connection anyway, and I'm limiting the speeds to not hog it from the other users in the house.

I'm not entirely sure I understand what you mean about the /home partition. I'm leaving /home inside each OS's / folder. I know that many programs create hidden folders within each user's home directory to use, so what I was thinking was to make a folder titled Shared within my home directory (eg. /home/johnsmith/Shared) and then mount the addition partition to that location. Then fill that with Music, Spreadsheets, PDFs, etc. 

As for making it unbootable without the USB device, that's mainly for fun. I found an old 256 and an old 512 the other day, so I'm trying to find uses for them. We recently discussed hardware tokens for logging into systems, and I thought that making one for booting might be fun to try.

And CDs/DVDs will work for installations. I keep some diagnostic ISOs and ISOLINUX on a multiboot device for netbooks, but the DVD drive on my computer is fine.

---

### Post by wilee-nilee on 2011-05-05
That wili be fun until you loose or forget the thumb and really need to get in, lol. ;)

I would set up the thumb with the boot like you want and have a bootable supergrub2 install as well that will get you in no matter what to all grub2 OS's windows and probably anything booting with grub-legacy. At least have a supergru2b available and or learn the manual cli to get in.
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

I assume you recognise as well that booting from a thumb is not protection, from another getting in, in the same amount of time it takes you, with an full read and write of everything.

As it is now you would have to wipe the mbr if you have installs now this is a risky endeavour, can be done, but you risk loosing anything on the hd if you mess up the partition tables.

This can be done, it is not difficult, but really you want to have some semi geek knowledge here to cover your booty.

If you want to be uber cool do it all from the cli.;)

After thinking about this I realised you may be already there. If you have a full install of a OS using grub2 on a thumb you would just run
sudo update-grub 
from the thumb install to to pick up any installs on the HD.

So you just need to wipe the mbr others can help with that. I would clone the set up you have now just top be safe in case the mbr being wiped causes problems.

Each additional linux os will have an option to install grub to a specific place or not at all, choose not at all, or back into the partition being installed to.

You can generally put the grub bootloader in the intalled partition with linux with no problems. I suspect this is the same with grub-legacy.

---

