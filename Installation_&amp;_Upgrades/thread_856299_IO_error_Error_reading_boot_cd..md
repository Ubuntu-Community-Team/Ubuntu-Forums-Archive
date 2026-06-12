---
title: "I/O error Error reading boot cd."
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by modchamp on 2008-07-11
Well I'm totally new to Ubuntu and Linux. I'm fed up with Windows and looking for a good alternative. Anyways I consider myself decently skilled with computers, fairly good with a couple programming languages, fluent in php, built my own pc, etc. Anyways I downloaded the ISO ubuntu-8.04.1-desktop-i386 and used InfraRecorder to burn it to a CD, but when I boot up my computer with the cd in the tray it comes up to the ubuntu menu, then no matter what I select (Install, Try Out, Check for Errors, etc) it says I/O Error, Error reading boot cd and gives me a button that says Reboot. I've tried burning the cd on 2 different computers with 3 different drives, 3 different ISO burning applications (InfraRecorder, MagicISO, and ISORecorder), on 4 different disks (1 Memorex CD-R, 3 Pengo CD-RW's), and 2 seperate downloads of the ISO. Yet all end up with the same error. So I'm asking, what could I be doing wrong and what should I try?

Oh I forgot this computer that I'm trying to install on has the following specs:
MSI K9VGM-V AM2 VIA K8M890 Micro ATX AMD Motherboard
AMD Athlon 64 X2 4400+ Brisbane 2.3GHz Socket AM2 65W Dual-Core Processor Model ADO4400DOBOX
Western Digital Caviar SE16 WD3200AAKS 320GB 7200 RPM SATA 3.0Gb/s Hard Drive
WINTEC AMPO 2GB 240-Pin DDR2 SDRAM DDR2 667 (PC2 5300) Desktop Memory Model 3AMD2667-2G2-R
Windows XP Home Edition Service Pack 2

The hard drive has 2 partitions, 1 with windows xp and 1 that's empty.

All help is appreciated, thanks very much.

-modchamp


Edit: Oh also I already checked the md5 hash on the ISO and it matches that of the site, though I'm not sure how to check the md5 hash on the cd.

---

### Post by avtolle on 2008-07-11
Since you have a SATA drive, the following has helped some in getting around similar problems.

First, read this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) especially the part about using boot options at installation time. Second, try this boot option: all_generic_ide which is to be added to the boot string as is the example shown in the link. If this works, you should be able to complete booting and begin installing.

If, after installing, the same problem presents itself on restarting, you may need to add the same boot option to the boot string, again using the procedure set out in the link (a bit further down the page). Good luck.

---

### Post by modchamp on 2008-07-11
Well I just tried that, and it seemed to take longer to get the error message but I still do get the error message.

---

### Post by avtolle on 2008-07-11
Going to where I should have started; before burning the iso to disk, did you check the md5sum of the iso file? 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by modchamp on 2008-07-11
Yeah, if you check a bit ago I added to my first post. I checked the md5sum of the iso I downloaded and it matched. Though I still haven't checked the md5sum of the disk, not quite sure how to do it.

---

### Post by avtolle on 2008-07-11
I'm seeing a few threads with similar problems involving the 8.04.1 iso. At least one indicated the 8.04 iso burned to CD worked, but the poster didn't want to deal with all the updates after installation. Have you given that (the 8.04 iso) any thought? I'm at a bit of a dead end here.

Not familiar with InfraRecorder or the other utilities you used to burn the CD, but I think one or more of them has a verification routine that should check the CD, once burned.

---

### Post by modchamp on 2008-07-11
You mean download ubuntu version 8.04? If so where can I find it? All I see is downloading 8.04.1 from the official site.

Not sure about verification, but I have burned it at 4x, 2x and 1x speeds as well as full speed and same result.

---

### Post by modchamp on 2008-07-11
Well I still didn't figure it out, but I used magicISO to mount the ISO and then just ran that from windows xp and installed it to the other partition. Thanks for the help.

---

### Post by cargman on 2009-05-16
...Sounds like the same problem I am having
 
I have a Dell Inspiron 6000
Intel Pentium M 1.6Ghz 2Gram.
 
I'm trying to install 9.04.
 
I get the intro screen where it gives me the starup menu:
 
Try Ubuntu without any change to your computer
Install Ubuntu
Check disk for defects
Test memory
Boot from first hard disk
 
If I select any of the first four selections it locks up and tells me
 
I/O Error
Error reading boot CD
 
 
I've tried burning CD's at slower speed and with different programs.  I get the same exact error.
 
 
I got the virtualclone drive and mounted the iso to my drive as well.... 
 
worked

---

### Post by Ayers on 2010-01-24
i have that same problem and im without an os...please help...i have a dell latitude

---

