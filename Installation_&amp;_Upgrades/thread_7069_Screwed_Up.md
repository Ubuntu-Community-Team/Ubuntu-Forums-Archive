---
title: "Screwed Up"
date: 2004-12-03
forum: Installation &amp; Upgrades
---

### Post by Blue Storm on 2004-12-03
Hello all,

I have a 200gb disk as my primary master and a 40gb as the primary slave. I had my master drive formated into four 40gb primary partitions so linux had issues trying to make another partition on the remaining space there. I had winXP installed on my primary drive. So I moved all files off my slave drive and installed Ubuntu on that, it put that grub loader somewhere and installation seemed to go OK except I only got a command line interface. When I booted up I didn't seem to get the optino to boot to windows, it would just go to linux and then go to a command line I just couldn't use. After removing ubuntu from the disk I booted up again and got grub loader telling me there was an error.

Can anyone tell me how I might get grub loader off the system so I can get back to my windows install?

---

### Post by mark on 2004-12-03
Hello - you might want to search the forum for the term *fixmbr*.  I'm not sure about XP, but with Windows 2000:

[list=1]
[*]Boot the Win2K CD-ROM
[*]Choose "Repair existing installation" (not sure of the wording here)
[*]Once at the Repair Console, enter *fixmbr* 
[/list] This rewrites the Windows master boot record (MBR) and all should be good.

---

### Post by Blue Storm on 2004-12-03
[QUOTE=mark]Hello - you might want to search the forum for the term *fixmbr*.  I'm not sure about XP, but with Windows 2000:

[list=1]
[*]Boot the Win2K CD-ROM
[*]Choose "Repair existing installation" (not sure of the wording here)
[*]Once at the Repair Console, enter *fixmbr* 
[/list] This rewrites the Windows master boot record (MBR) and all should be good.[/QUOTE]
 Ah, ha. Fixed all my problems. Many thanks my friend. ^^

---

