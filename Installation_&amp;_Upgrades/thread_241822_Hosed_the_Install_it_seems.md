---
title: "Hosed the Install it seems"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by Recked on 2006-08-22
Hello,

I got Ubtuntu installed without hitch on my laptop :D , but for some reason on my Dell Workstation which still has Windows XP on the main partition I now get as far as to the grub> prompt and no further after the install finished without any issues.

Why doesn't Ubuntu ask where to load Grub as other distros do and what has happened now to my Dell machine?

Any help would be appreciated.

thanks

---

### Post by ma-martin on 2006-08-28
Did you ever resolve this problem?  I'm having the same issue with a Dell Dimension 8100.

---

### Post by Recked on 2006-08-29
Hey,

Yes I did last night. I downloaded a Windows 98 emergency disk and ran when inserted and the machine booted to the floppy drive (the emergency disk). I was brought to an A:\ prompt where I issued the command A:\FISK.EXE /MBR which fixed the master boot record for Windows. I then rebooted and Windows XP came back up without issues. I removed all linux partitions and am waiting to see if I am in the mood to fuss with Ubuntu again and try to get it to install without issues next to XP.

Not sure how other folks are doing it but it (Ubuntu install routine) clearly does not ask what/where to install Grub and this is what caused the issue for me.

Hope this helps.

Thanks

---

