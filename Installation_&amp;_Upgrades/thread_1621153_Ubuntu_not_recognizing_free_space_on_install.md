---
title: "Ubuntu not recognizing free space on install"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by Wheels2050 on 2010-11-13
Hello all, I would appreciate some help with installation of ubuntu 10.04. Here's what happened:

I had ubuntu 8.10 installed, but support was no longer offered - I wasn't able to upgrade software etc. I decided to upgrade to 10.04 today. I made the boot disk as normal, but when I went to install it I got the message "This computer has no operating systems installed". The only options were to wipe the entire hard drive or create my own partitions.

I have Windows Vista installed, so I deleted the partition which had ubuntu 8.10 (and also the swap file partition) so I now have free space on the computer. However, in Vista this shows up as an extended partition with Dell MediaDirect.

When I go back to the 10.04 installer, it still does not recognize my Vista installation, and only gives me the option of wiping the HDD. From googling and searching these forums, it appears as though the problem is that the free space and the Dell MediaDirect partitions overlap and this is why the free space is not recognized by ubuntu. Can anyone please offer any advice?

Thanks very much,
Ben

---

### Post by bryanl on 2010-11-14
I don't think the media direct is the issue and I don't know what you did to delete the old Ubuntu partition so take that as a caveat for what I suggest.

Boot the Ubuntu disk and select trial so you can get a system. In the system menu, you'll find a partition editor that will let you see what you've got on the disk. You should have an NTFS partition with your Vista system and perhaps another NTFS with a OEM recovery partition. 

If there is free space on the drive, you can create partitions in it for the Ubuntu install. If not, you'll need to resize the Vista partition to shrink it down to get some free space. 

I like to set up a partition of about 15 GB for root and the remainder as a partition for /home. I use a swapfile instead of a separate swap partition (see [http://tcl.leipper.org/?p=992](http://tcl.leipper.org/?p=992) ) but you can create a swap partition of you want to go that way.

Once you know you have a partition for Ubuntu, run the install and use the manual partition option. That will bring up a partition editor showing you the partitions you have on your hard drive so you can select the one where you want the system to be and so on. Click the edit button and tell it the mount point, file system to use, and whether or not to format that partition.

Once you have that done, it should be just a case of let the installer load the partitions.

unless I am missing something ....

---

### Post by Wheels2050 on 2010-11-14
Thanks a lot for the reply bryanl. I've managed to fix it by removing the mediadirect partition, which then allowed ubuntu to recognize the free space and install.

I think what happened was that the free space, on which the old ubuntu installation was located, was somehow joined with the mediadirect partition as an extended one which ubuntu wouldn't recognize.

Thanks again for the quick reply though!

---

