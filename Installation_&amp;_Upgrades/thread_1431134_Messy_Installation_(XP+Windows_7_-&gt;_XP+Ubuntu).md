---
title: "Messy Installation (XP+Windows 7 -&gt; XP+Ubuntu)"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by Plague on 2010-03-16
Hi,

I had Windows XP installed on a SATA HDD and Windows 7 Ultimate on an IDE HDD. I wanted to installed Ubuntu 9.10 on the same HDD as Windows 7 but the option "Install side by side..." was showing only the SATA HDD. I choose the option of deleting everything on the IDE HDD and installing Ubunut on it. It installed, but now in the boot menu I get the option of choosing between Windows 7 and Windows XP. To boot Ubuntu I have to select to boot from the IDE HDD.

I was wondering if there is a way to clean up this mess. I want the boot menu changed so I have the option of choosing between Ubuntu and Windows XP.

I tried modifying the boot.ini file on Windows XP, but it only has Windows XP listed. I tried modifying menu.lst on Ubuntu but it does not exist.

Any help would be greatly appreciated.

Cheers

---

### Post by djchandler on 2010-03-16
What happens if you choose Windows 7 from the NT Bootloader menu?

Did you follow these steps?

[http://support.microsoft.com/kb/q289022/](http://support.microsoft.com/kb/q289022/)

---

### Post by Plague on 2010-03-16
> **djchandler said:**
> What happens if you choose Windows 7 from the NT Bootloader menu?

It says it is damaged and request that I insert the CD to fix it. I chose to format the IDE HDD Windows 7 was installed on and installed Ubuntu on it. Ubuntu also shows Windows 7 as a boot option. I have not selected that one but am guessing it won't do anything either.

I tried to search if anyone else had come across the same problem but did not find anything.

---

### Post by djchandler on 2010-03-16
Try this:

[http://vlaurie.com/computers2/Articles/bootini.htm](http://vlaurie.com/computers2/Articles/bootini.htm)

And this article specifically talks about 2 operating systems on 2 different drives.

[http://www.linux.com/archive/articles/113945](http://www.linux.com/archive/articles/113945)

This solution isn't simple, but neither is your particular problem. But it does show how to link to GRUB on the second drive from the NT bootloader on the first drive.

Good luck!

---

