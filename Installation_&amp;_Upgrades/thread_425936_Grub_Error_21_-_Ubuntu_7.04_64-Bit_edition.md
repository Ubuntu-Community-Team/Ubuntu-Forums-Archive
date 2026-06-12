---
title: "Grub Error 21 - Ubuntu 7.04 64-Bit edition"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by chrisbain88 on 2007-04-28
Hi,
I have downloaded and decided to install 7.04 64-bit on my Intel Core 2 Duo E6300 as a dual boot with windows XP pro.
I installed XP first and then ubuntu.
upon restarting my computer after the completion of the ubuntu installation i receive the Grub Error 21 message

"GRUB Loading Stage1.5.

GRUB loading, please wait...
Error 21"

i have already tried reinstalling ubuntu on its partition after formating it and i receive the same message.
has anyone got a solution to this problem.
help is greatly appreciated
Thanks
Chris

I add that i am using a Asus P5B Green motherboard and an IDE hdd

---

### Post by msandersen on 2007-04-28
Error 21 means the disk doesn't exist as far as it knows.

You could try this from the Mepis forum:
[http://www.mepis.org/node/5782](http://www.mepis.org/node/5782)
[http://www.mepis.org/node/7330](http://www.mepis.org/node/7330)

As an aside: Here's how you can use the Windows boot manager:
[http://www.tprthai.net/bootmgr.htm](http://www.tprthai.net/bootmgr.htm)
Or if you have NTFS-3G installed:
[http://www.mepis.org/docs/en/index.php/Windows_boot_loader](http://www.mepis.org/docs/en/index.php/Windows_boot_loader)

---

### Post by surfingchimp on 2007-04-28
I get this same problem.

I have RAID 0 on a promise fastrack controller

when I go to install ubuntu it detects 2 harddrives, but those 2 drives are ment to be striped and as 1, I am guessing this is why it is failing.

any help greatly appreciated

---

### Post by chrisbain88 on 2007-05-04
Hey All

I found the problem!!
I have an Asus P5B Green motherboard and it is primarily a SATA board and i am running and IDE hdd on the only IDE controller.
I read somewhere that the Grub boot loader looks at the bios to determine hdd details. in my bios where on the older motherboards IDE drives and there details appear i have the SATA controllers.
Hence the Error 21 (disk does not exist). Thanks msandersen for pointing me in the right direction.
Therefore solution, purchase a SATA hdd and run my OS's off that.

Cheers
Chris

---

