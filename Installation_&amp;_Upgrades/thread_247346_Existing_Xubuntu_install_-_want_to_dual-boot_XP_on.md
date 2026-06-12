---
title: "Existing Xubuntu install - want to dual-boot XP on a new hard drive"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by Super King on 2006-08-30
I have been running Xubuntu on a 20 GB IDE disk drive, and am planning on running a dual-boot setup with Windows XP installed on my new 80 GB SATA drive. I have previously setup a dual-boot environment with both OS's on the save drive and Windows installed first (following directions from the Ubuntu Wiki), but this is different as I'd like to keep my existing drive with Xubuntu and leave Windows to its own drive. 

I've read that the Windows bootloader often messes things up, and I'd like to stick with GRUB. Is this possible? If the Win bootloader takes over and doesn't allow we access to the Xubuntu disk, would I be able to say, use a *Buntu live CD, mount the Xub. drive, make GRUB the primary bootloader (by messing with menu.lst or whatever), and then have the result be a proper dual-boot with GRUB (with each OS on its own drive)?

Thanks :mrgreen:

---

### Post by randell6564 on 2006-08-30
> **Super King said:**
> I have been running Xubuntu on a 20 GB IDE disk drive, and am planning on running a dual-boot setup with Windows XP installed on my new 80 GB SATA drive. I have previously setup a dual-boot environment with both OS's on the save drive and Windows installed first (following directions from the Ubuntu Wiki), but this is different as I'd like to keep my existing drive with Xubuntu and leave Windows to its own drive. 

I've read that the Windows bootloader often messes things up, and I'd like to stick with GRUB. Is this possible? If the Win bootloader takes over and doesn't allow we access to the Xubuntu disk, would I be able to say, use a *Buntu live CD, mount the Xub. drive, make GRUB the primary bootloader (by messing with menu.lst or whatever), and then have the result be a proper dual-boot with GRUB (with each OS on its own drive)?

Thanks :mrgreen:

Read this before moving forward [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)  Good Luck!

---

### Post by Super King on 2006-08-30
Hmm, after all that I decided to just reinstall both OS's on the same drive :)

I've ran into a problem though: when I get to the partioner part (of the text install), I am unable to actually resize my XP partition. I choose it, select resize, choose an applicable size (40 GB), but when I hit continue, it doesn't actually go through the resize process. Rather, it kicks me back to the main partitioning screen. Am I doing something wrong?

---

### Post by randell6564 on 2006-08-31
> **Super King said:**
> Hmm, after all that I decided to just reinstall both OS's on the same drive :)

I've ran into a problem though: when I get to the partioner part (of the text install), I am unable to actually resize my XP partition. I choose it, select resize, choose an applicable size (40 GB), but when I hit continue, it doesn't actually go through the resize process. Rather, it kicks me back to the main partitioning screen. Am I doing something wrong?

Well, it still sounds like a Raid problem, but if you are reinstalling both OS's, why do you still need to resize your windows partiton?

If you are going to reinstall then just wipe the drive, partition it and install windows first, then ubuntu.

---

### Post by Super King on 2006-08-31
Sorry, don't think I was clear enough, that is what I'm doing. I have installed Windows and I am running through the Ubuntu text installer. I get up to the point where I'm asked to partition. I *think* what I should be doing is choosing the 'resize the partition' option on the Windows (picture 11 on this [site]("http://users.bigpond.net.au/hermanzone/p3.htm") is where I'm at in the installer). I get to the part where I can set the size for the partition (picture 13 on that site) but after I choose the size and press enter, instead of seeing the long resizing process (with progress bar, etc.) I'm just flipped back to the first partition page. Seems weird.

I will be burning a new live CD to try the install from there again, but it locked up when I tried it previously so I'm not sure how well that will go.

---

### Post by randell6564 on 2006-08-31
> **Super King said:**
> Sorry, don't think I was clear enough, that is what I'm doing. I have installed Windows and I am running through the Ubuntu text installer. I get up to the point where I'm asked to partition. I *think* what I should be doing is choosing the 'resize the partition' option on the Windows (picture 11 on this [site]("http://users.bigpond.net.au/hermanzone/p3.htm") is where I'm at in the installer). I get to the part where I can set the size for the partition (picture 13 on that site) but after I choose the size and press enter, instead of seeing the long resizing process (with progress bar, etc.) I'm just flipped back to the first partition page. Seems weird.

I will be burning a new live CD to try the install from there again, but it locked up when I tried it previously so I'm not sure how well that will go.

So, you DID wipe your drive and reinstall windows?  If that is the case then you should have partitioned your drive BEFORE installing anything.
That way you would not have to be dealing with any resizing!

with a clean, partitioned drive, you should have put windows on one and ubuntu on the other.  Partition BEFORE installing.

---

### Post by confused57 on 2006-08-31
You "might" be able to resize the Windows partition using the gparted live cd(approx 30 mb download):

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

If you change your mind and want to install each OS on a different drive, this may give you an option:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

