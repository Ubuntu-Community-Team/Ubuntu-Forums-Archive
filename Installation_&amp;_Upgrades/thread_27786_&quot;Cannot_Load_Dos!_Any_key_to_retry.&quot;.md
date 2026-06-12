---
title: "&quot;Cannot Load Dos! Any key to retry.&quot;"
date: 2005-04-17
forum: Installation &amp; Upgrades
---

### Post by taxpayer on 2005-04-17
That's the message I get trying to boot from the installation cd.  Any key, of course, merely results in the message repeating.  When I remove the cd from the drive, then any key results in booting of XP.

The computer I'm trying to install on already has Windows XP (I hope to end up with a dual-boot machine).  The 200 gb drive is partitioned in three parts, of which one is NTFS for Windows and the others are (currently) empty.  I have an AMD64 chip (3400+) and am using the AMD64 install CD, which I downloaded.  

The live cd works fine; just the install cd (which I wrote with the same program and made bootable) has the problem.  XP still works, as well as ever.  Bios is AMI 1004.005, and I have verified that it is set with the cd-rom as first priority.  DOS "FC" says that the file on the cd is a true copy of what I downloaded. 

I can't find any indication that anyone's ever had this particular error when trying to install Linux.  Any suggestions what I should try next?

---

### Post by andvaranaut on 2005-04-17
Hi taxpayer

How did you write the CD? When you open the CD with Windows Explorer or something similar, you should see a bunch of files. If you only see a single file (a .iso), you did not record the CD correctly.

You must write the CD using the "write image" option of your CD-writing program. In fact, you should not be given the option of making the image bootable; if you do, you probably are writing the .iso image as a regular file, not as a CD image.

Try again (maybe with a CD-RW) with the "write image" option and see if it works.

Hope this helps, andvaranaut.

---

### Post by taxpayer on 2005-04-17
Thanks, andvaranaut, that did solve the problem.  I guess "bootable" means "bootable from dos (windows?).  

My new problem deserves a thread of its own.

---

