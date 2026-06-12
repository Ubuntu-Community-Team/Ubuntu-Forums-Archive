---
title: "Grub Error 21"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by n0madic on 2007-07-18
I have gotten myself into some what of a pickle...
I have a 4 GB flash drive that I wanted to install Ubuntu (Feisty Fawn) onto. I got the .iso file and burned it onto a CD and then installed it onto my flash drive. Now when I go to restard after a succesful install I get this:
GRUB Loading stage1.5.

Loading GRUB, please wait... 
Error 21

So now I can't get on the local OS (Windows) and the only way to boot up Ubuntu is the live CD. Also, I can't get into the BIOS (making things even more complicated)

Please any help would be greatly appreciated!

P.S. The faster I can do this before my dad finds out the better:)

---

### Post by confused57 on 2007-07-18
> **n0madic said:**
> I have gotten myself into some what of a pickle...
I have a 4 GB flash drive that I wanted to install Ubuntu (Feisty Fawn) onto. I got the .iso file and burned it onto a CD and then installed it onto my flash drive. Now when I go to restard after a succesful install I get this:
GRUB Loading stage1.5.

Loading GRUB, please wait... 
Error 21

So now I can't get on the local OS (Windows) and the only way to boot up Ubuntu is the live CD. Also, I can't get into the BIOS (making things even more complicated)

Please any help would be greatly appreciated!

P.S. The faster I can do this before my dad finds out the better:)
What happened is that grub's IPL was installed to the internal hard drive's mbr.  There are several ways to restore Window's IPL to the internal hard drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The easiest is with a Windows XP install cd(not a recovery cd), enter recovery mode by pressing "r", then the command FIXMBR should restore your Window's mbr.

If you have access to another computer the Super Grub Disk can do this.

---

### Post by n0madic on 2007-07-18
Im going to try the Super Grub Disk (I don't want to use Windows unless I have to), I'll post back after giving that a try.

Thanks

edit//

If you have any knowledge of how to restore it using SGD please explain

edit again//
problem solved, thanks a lot!

---

