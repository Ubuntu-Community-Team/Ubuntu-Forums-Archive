---
title: "Can't check Windows 7 for errors because Grub is blocking it"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Morty007 on 2010-05-19
Dual booting Mint 8 and Windows 7.

Windows is reporting a file system error. I go into properties and check for errors, but since it's in use it asks me to reboot. I do, and grub comes up. I select windows and it just takes me to windows without checking the file system.

I then put in the windows dvd and do chkdsk. It tells me something to the effect that the current drive is locked or cannot continue. (I just don't remember, this problem is ongoing for about a month.)

I googled and it said something about dispart.exe. I do that and input some commands and you can see from the picture what happened. [[img]http://xs.to/thumb-8BCF_4BE634BA.jpg[/img]](http://xs.to/share-8BCF_4BE634BA.html)

Should I just do a fix mbr? I want to fix the errors before installing mint 9.(It's ok if grub gets wiped out because I'm planning on installing the new mint 9.)

---

### Post by oldfred on 2010-05-19
It was my understanding that you have to run checkdisk until you get no errors. 

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

