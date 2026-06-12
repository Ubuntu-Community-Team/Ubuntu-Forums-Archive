---
title: "[SOLVED] Keep getting errors on install cd, 64-bit 8.10"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by murak on 2008-11-06
When I burn Ubuntu 64-bit Desktop I get errors on the cd. 

Burning process is always ok, no problems, then when I boot up and scan the cd for errors there are 1, 2 or 3 errors wich makes an installation impossible. I tried a number of different download locations, different ubuntu versions (xubuntu, ubuntu daily etc) different cd media, different cd-drives on two different computers, different cd writing speeds. I also tried the USB option, same thing :(

Asus P5Q intel P45
Celeron E1200
8gb corsair xms2 PC6400
Sapphire 4850 dualslot
WD Raptor 74gb

No OC yet.

UPDATE: Checking the cd in another pc resulted in no errors! So the cd is fine, its my computer that is the problem. I installed vista (hey I was desperate) wich installed just fine, but almost every program I download cant be installed because the file is corrupt. Aha! So some part in my pc is missfireing. I did a memtest (from the ubuntu live cd) overnight and there where no errors, so ram is fine. Then I tested HD tune (hd diagnostics tool) wich said my hd was fine. Also, I downloaded AVG (antivirus) to another pc and tried to install it on mine but the file was corrupt, so I tested it on the other pc and it was fine! It installed just like it was supposed to. So there is defenetly something wrong with my pc, but what?

Will now do some cpu testing, first everest.

Any suggestions warmly welcome, I have lots and lots of time and patiens.

---

### Post by jill.valentine on 2008-11-06
well, you haven't say about writing cd's from other cdrw. have you tried on another cd writers??? maybe your cdrw have some problem.

---

### Post by murak on 2008-11-06
> **jill.valentine said:**
> well, you haven't say about writing cd's from other cdrw. have you tried on another cd writers??? maybe your cdrw have some problem.

Thank you for your quick reply. I tried two different cd medias, no cdrw though. And I tried tree different cd writers. Ill download the iso at a friends house and burn it there.

---

### Post by rob99 on 2008-11-06
I´ve had the same problem using both the normal and alternate CDs for 64bit 8.10. Trying to add the CD as a Software Source gives the following error message:

> Error scanning the CD

E:Could not open file /cdrom/dists/intrepid/main/binary-amd64/Packages - open (2 No such file or directory), E:Unable to determine the file size - fstat (9 Bad file descriptor), W:Hash mismatch for: main/binary-amd64/Packages, E:Could not open file /cdrom/dists/intrepid/main/debian-installer/binary-amd64/Packages - open (2 No such file or directory), E:Unable to determine the file size - fstat (9 Bad file descriptor), W:Hash mismatch for: main/debian-installer/binary-amd64/Packages, E:Could not open file /cdrom/dists/intrepid/restricted/binary-amd64/Packages - open (2 No such file or directory), E:Unable to determine the file size - fstat (9 Bad file descriptor), W:Hash mismatch for: restricted/binary-amd64/Packages, E:Could not open file /cdrom/dists/intrepid/restricted/debian-installer/binary-amd64/Packages - open (2 No such file or directory), E:Unable to determine the file size - fstat (9 Bad file descriptor)

---

### Post by murak on 2008-11-09
Alright, we are getting closer =) I pulled out two of the 4 sticks of ram and then ubuntu installed just fine! So, its my mb that has a problem with 4 sticks of ram. 

I will make a new thread about it on asus forum.

Thanks everyone who partitipated in this thread!

---

