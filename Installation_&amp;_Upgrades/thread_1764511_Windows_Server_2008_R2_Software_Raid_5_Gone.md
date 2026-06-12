---
title: "Windows Server 2008 R2 Software Raid 5 Gone?"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by I12crash on 2011-05-21
I just replaced Windows Server with Ubuntu 11.04 on my HTPC Server. I have a 32GB SSD (OS Drive), 1TB drive for my daughters movies and music, and 3 2TB drives that were in a software raid 5 in windows server. After formatting the OS drive and installing ubuntu 11.04 my raid 5 drive is gone. I can't even see the drives. Is there a way to fix this? Am I just out of luck and have to format and reconfigure the raid? Any help would be really appreciated.

---

### Post by I12crash on 2011-05-22
bump..does no one know the answer this?

---

### Post by A1defiant on 2011-12-01
Over a year too late.

But... just had the same issue. Easy to sort out. Reinstall Windows 2008 and all RAID 5 works after you import the now foreign discs back into windows 2008

---

### Post by darkod on 2011-12-02
To ask the obvious question (if someone googles this in the future), why would anyone expect a software raid created in one OS to be recognized when you install a completely different OS on the OS disk?

The term software raid means the software (OS) is creating it and you can't expect another totally different OS to pick it up.

---

