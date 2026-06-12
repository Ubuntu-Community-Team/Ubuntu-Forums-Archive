---
title: "HDD not recognized"
date: 2015-05-22
forum: Installation &amp; Upgrades
---

### Post by Eddy_Ingleton_Vinc on 2015-05-22
I have a Packardbell computer that came with a preinstalled version of Windows 8. I decided to install ubuntu instead and made a clean install where i allowed the ubuntu installer to format the entire drive and make an ubuntu install. But now my computer doesnt recognize my HDD. Instead it gives me the option of choosing an unknown device (which is my ubuntu system) and when i choose it ubuntu starts up ;) so it works but my computer doesnt recognize my HDD as being the HDD on the computer! What do i do? :mad:

---

### Post by dino99 on 2015-05-22
some brands sadly sometimes "tatooed" their hdd/hardware as they made a deal with a specific OS corp. They set a 'hidden' partition on the hdd, and a normal 'format' does not remove it. The solution is to first check into the bios if that hdd is well identified, then go for a 'low format'

[http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/](http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/)

when that steps have been successfull, you then need to redo the normal steps for formatting/installing (better the 'something else' option of the ubuntu installer to do a custom partitionning: a / (root) partition, ext4, boot flag, about 15 gb, a swap partition about 4 gb, and a /home partition, ext4 to store your data & settings). Usually with a hdd < 2To (non gpt) a primary partition is set, then an 'extended' one where the other ones are created (bypass the 4 primary limits).

---

