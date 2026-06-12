---
title: "Installed 11.10, Windows 7 won't start"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by colbygatte on 2011-10-17
Windows 7 will go as far as the load screen, with the Microsoft logo. After that, there is a flash of a blue screen with text (so fast I can't read it) and then back to the bootloader.

---

### Post by Mark Phelps on 2011-10-18
Not telling us much useful ...

HOW did you install 11.10?  I'm guessing you used the side-by-side option and the slider to shrink Win7, right?

IF so, you got the unfortunate side-effect of a corrupted NTFS filesystem on your Win7 OS partition -- which happens sometimes when the Ubuntu installer shrinks that partition.

If you had used the Backup feature in Win7 when it worked, you could have created and burned a FREE Win7 Repair CD -- which you could now use to restore Win7 boot.

Since you didn't do that, you will need to go to the link below, select the proper Win7 version, PURCHASE the disk image, download it, and burn it to CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

THEN, boot from that CD and run Startup Repair at least three times. That should restore Win7 boot for you.

---

### Post by Bmonsterboy on 2011-10-18
Have you tried to use win7 under safe mode? If that works, then login and do a system restore.

---

