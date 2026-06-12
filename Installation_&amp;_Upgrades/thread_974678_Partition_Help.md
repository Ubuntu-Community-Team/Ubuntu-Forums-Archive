---
title: "Partition Help"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by green_kev on 2008-11-07
Hey guys, 
I have some partition issues, and would like to have your advice or help so I may resolve them. As of right now my hard drive is partitioned Ubuntu occupies 200 GB and 50 are supposed to be for Vista. However, I have yet to install Vista but would like to do so now, thing is when i pop the cd it says "windows is unable to find a system volume that meets its criteria for installation". Also when I look at the hard drives in the partitioned editor it says 1.91 GB are set for linux swap, 186.26 GB for ext3 of which 5.06 have been used up. Finally the third hard drive says ntfs and it has 44.71 GB unused. In addition, ntfs has a small warning sign next to.

Now that I've explained my situation here are my questions:
1) Is there a tutorial, guide I can follow or anything I can do so that Vista will be safely installed in the 44.71 GB and not jeopardizing Ubuntu?

2) Should I leave things be and follow the advice given to in the response to the first question or should I delete NTFS in the Ubuntu partition editor and then proceed to install Vista?

3) If what I've detailed in question 2, is the best option, once I hit delete and then apply, how do I install Vista in the newly unallocated space in my hard drive?

I know I have a lot of problems and multiple questions but I really need to get this issue resolved.

Thanks in advance for any help provided

---

### Post by Idefix82 on 2008-11-07
First of all, Vista will probably be happier if you delete the NTFS partition and let Vista create its partition itself.

Second, be warned that Vista will kick GRUB out of the boot sector, meaning that when you start your computer you won't see the Ubuntu installation, you will simply boot into Vista. To restore GRUB you can follow this guide for example: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Third: it's a lot of hassle for a system which you won't like if you have spent any time with Ubuntu :)

---

### Post by cdtech on 2008-11-07
Personally I would format to install Vista then use Vista to allocate the space needed for Ubuntu. Vista is very picky about being the only OS on the drive.

After the allocation you can install Ubuntu to the space provided by Vista and all is well.

---

### Post by Idefix82 on 2008-11-07
But as I read the first post, he already has Ubuntu installed. That's why I said that it's a lot of hassle for a rubbish system which will try to force him to abandon the better OS.

---

### Post by cdtech on 2008-11-07
> **Idefix82 said:**
> But as I read the first post, he already has Ubuntu installed. That's why I said that it's a lot of hassle for a rubbish system which will try to force him to abandon the better OS.

My bad, I just re-read his post......

---

### Post by caljohnsmith on 2008-11-08
Here are some thoughts of why you may be getting the "windows is unable to find a system volume that meets its criteria for installation" error:
[LIST]
[*]Windows normally needs to be installed to a master drive, but it is possible to install Windows to a slave drive if you have a FAT/NTFS partition on the primary drive where Windows can put its boot files.
[*]Also, you should install Windows to a primary partition, because if try to install Windows to a logical partition, (again) Windows will insist on putting its boot files in a primary partition on the master drive.
[*]If you have no choice but to install Windows to a slave drive or logical partition, it is possible to move the Windows boot files back to the Windows partition after the installation is done, run a few commands from the Vista Install CD, and then get Vista to boot entirely from its own partition.[/LIST]
And of course as Idefix82 mentioned, you might have to reinstall Grub since Vista will install its own MBR (Master Boot Record) to the boot drive. Anyway, let us know how it goes. :)

---

