---
title: "Windows XP and Ubuntu dual boot problem"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by jamberu on 2005-07-11
Hello,

I was wondering if someone would be able to help me with a Windows XP / Ubuntu dual boot problem.

I have been using Ubuntu for a while but the install seemed to have locked out my XP install so I decided to completely start again today. I deleted the Windows partition and reinstalled it which went fine and then went to install Ubuntu on the second partition I have on the same hard drive. The trouble is when I install Ubuntu it all goes fine until the boot when it presents me with a message that

Grub loading, please wait….
Error 18

I have fixed the mbr using the recovery console and reinstalled I have even tried the method on the wiki to recover after a windows install (using the live CD to manually install grub).

I currently have nothing on the laptop so I am in a position where I could completely start again, but I have no idea what that error 18 means. If anyone has any ideas I would be very grateful.

Thanks in advance,

Duncan

---

### Post by not_yet on 2005-07-11
does this help?

Gr> grub error 18 

info grub wrote: 
18 : Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 
Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range). 

---

### Post by mingus on 2005-07-11
This means that your BIOS is constrained by the 1024 cylinder boundary, and the Ubuntu boot sector is located beyond that.  Therefore first check in your BIOS that you have LBA enabled; this may solve the problem.  If not, then get into Ubuntu and reinstall grub using the "--force-lba" option.  If this doesn't work, there are other options, but try these two first.

---

### Post by jamberu on 2005-07-12
Thanks for the replies guys, especially Mingus I think you tried to help me when I had the problem a couple of weeks ago. 

I’m going to admit defeat though, as reinstalling Ubuntu has now caused Windows to fail to boot as well. I need to get on with my project so I have completely removed windows and just have Ubuntu installed now. I’m going to try and see if Openoffice can hold up to writing my thesis, throwing it in at the deep end so to speak.


Duncan

---

### Post by mingus on 2005-07-12
Duncan,

Good luck re taking the Linux plunge . . . fwiw in the future re your 1024 problem, which was a common problem until just a couple of years ago . . . the solution is to create partitions one for XP and the other for the /boot directory of Ubuntu, both inside the 1024 limit.  Not hard to do if installing clean.  A second solution is to set up a dual-boot from inside the W$ install on the first partition; also fairly simple to do.  If you ever decide to go this route, let us know and we'll show you how.

---

