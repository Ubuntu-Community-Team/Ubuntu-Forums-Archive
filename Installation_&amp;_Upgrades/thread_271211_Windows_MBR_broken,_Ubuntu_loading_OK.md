---
title: "Windows MBR broken, Ubuntu loading OK"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by Thenotsowyzewun on 2006-10-04
Hi,

I installed Windows XP, then Windows Server 2003, then Ubuntu, then Windows XP, and already had Windows 2000 installed from ages ago.
So I looked at all this on my gigantic HDD (all on different partitions) and thought blimey what a state!
I obtained a Partition Manager for Windows (Ubuntu isn't online yet, wireless troubles (I've got another thread) and went about shifting my files about (in Windows Explorer) deleting lots and lots of stuff and deleting, resizing etc partitions.
That all went splendidly well, my partition's are all how I want them now.
Unfortunately, I wiped out the MBR in the process, so when I click Windows in GRUB it can't load.
How should I go about fixing this? I could just restore the MBR in the standard windows rescue console way but wouldn't that lose GRUB?
I would give you GRUB's current config btw, but I can't find it (tried Googling for it too, to no avail :( ).

---

### Post by divague on 2006-10-04
restore mbr and use this guide to reload grub

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by divague on 2006-10-04
restore mbr and use this guide to reload grub

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by Thenotsowyzewun on 2006-10-04
Thanks :)

---

