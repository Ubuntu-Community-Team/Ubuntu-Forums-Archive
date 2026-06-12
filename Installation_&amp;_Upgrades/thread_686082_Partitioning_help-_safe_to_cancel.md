---
title: "Partitioning help- safe to cancel?"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by junkmailking2k on 2008-02-02
I am currently shrinking my NTFS partition from 80 to 70 gb using a gparted live cd, After running for an entire day, the process finally completes and then starts all over again. Is this supposed to happen? I tried to cancel, but I get a warning saying that doing so will cause significant file system damage so I decided to let it continue. Is it safe for me to go ahead and cancel? Could I potentially lose data on my ntfs hard drive?
Any help would be greatly greatly appreciated. I really don't want to lose my data.
Thank you.

---

### Post by junkmailking2k on 2008-02-02
Once again, I would greatly appreciate any kind of help. I'm really worried I killed my hard drive :(
Can I safely cancel or will my hard drive data be ruined?
Is there anything I can do now to get my data out (its in the process of shrinking right now)?

---

### Post by louieb on 2008-02-02
I think I'd be worried too. Its not normal to run that long. Just shrunk  the NTFS partition on my laptop from 14 GIG to 10 GIG took less that an hour. 

If you cancel windows may still boot. But I think your probably going to need a program like testdisk  to repair the partition table. 
available on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page").

Also there is a good chance you can boot to a live CD and copy your data off if you wind up having to reinstall XP. [How do I copy data from a Winpartition to a USB harddrive using Ubuntu 6.10 Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=364493&highlight=copy+%26amp%3B+data")

Kinda out of date now it even easier with the Ubuntu live CD. My personal choice is the [Knoppix Linux]("http://www.knoppix.net/") or [Puppy Linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1") live CD's

---

