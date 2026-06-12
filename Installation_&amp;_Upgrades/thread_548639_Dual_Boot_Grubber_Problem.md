---
title: "Dual Boot Grubber Problem"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by vatsu on 2007-09-11
Intsalled Ubuto on my USB Drive, plugged into my Laptop running XP. I now get a GRUB boot loader window wherein I can make a choice between Ubuto or XP. PROBLEM : I cannot load my XP when I do not have the USB HDD plugged in. I get an error and I am not able to load XP. Can I fix this. If not, can I restore setting to my original state, wherein I can load my laptop to XP.

I get error Grub Error 21

---

### Post by dabl on 2007-09-11
There's a lot of Grub "how tos" on this thread: [http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by louieb on 2007-09-11
In a nut shell this is what happened. When you installed Ubuntu it overwrote the  MBR of your hard drive. THe first 466 bytes of the MBR is a pointer to the boot manager/loader program. Now it points to the GRUB program stage2 on your USB drive. 

To get it to boot XP again you need to change  the MBR back to pointing to the windows program ntldr. The   [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") can do this. Or you can  use your XP CD boot to the recover console and run fixmbr. 
Lots of ways described here. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by vatsu on 2007-09-11
Thanks every1, I was able to fix this using SuperGRUB disk. New 2 all this!

---

