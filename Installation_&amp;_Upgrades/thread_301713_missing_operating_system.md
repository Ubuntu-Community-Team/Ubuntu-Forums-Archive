---
title: "missing operating system"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by sabreman on 2006-11-17
Hi,
I've got a Compaq Deskpro Enseries SFF Pentium 2 computer and I was getting on quite well with the installation of Ubuntu Server.  Not being skilled at this I referred to comments on the sites that indicated the error messages I was getting were due to a corrupt download copy, I downloaded the iso at a high speed.  So after about an hour and multiple error messages, the installation was at about 6% so I litterally pulled the plug and gave up for the night.  I have now started again but there is no operating system recognised as the computer boots up.  Obviosuly I've made a mess of things but is there anyway to resolve this issue and how would I go about it?!
Thanks

---

### Post by NetworkGuy on 2006-11-17
Verify the ISO you downloaded is correct by checking the md5.

Burn the image at low speed (4x) to a CD.

Make sure you computer is set to boot from the CD before it tries the hard drive.

Hope this helps..

---

### Post by Herman on 2006-11-17
[CENTER]
Yeah, and before you begin your install, select 'Check CD for defects' too.
[/CENTER]
 
I recently had some problems with the new 'Edgy Alternate CD' and was blaming the software, until I finally went out and bought brand new CD-RWs. The .iso was passing the md5sum test, but the CD was failing at the same point in the install, (red screens with error messages). In spite of re-burning, and it kept failing the 'Check CD for defects' test with the same error. I re-burned it and I'm pretty sure I even tried burning it to different disks too, but still the same problem. Finally, now i have a good burn on a brand new CD-RW from exactly the same .iso file, and I have installed successfully from it. So there wasn't anything wrong with the software at all. It makes me wonder about the weird problems some people have though. What if they didn't check the CD for defects and it was good enough to complete an install, but it makes a faulty install. 

So, always use the 'Check CD for defects' option before beginning an install. :D

> I have now started again but there is no operating system recognised as the computer boots up. Obviosuly I've made a mess of things but is there anyway to resolve this issue and how would I go about it?! Normally, you just boot the installation CD again and go through the first several questions you are given untli you come to partitioning. Then, use the partitioner to re-format the faulty partitions, or  you can delete them and make them again if you want to be sure. Make sure you don't touch any FAT32 or NTFS partitions though, as those will be Windows, naturally.

Regards, Herman :D

---

### Post by sabreman on 2006-11-17
Thanks for feedback and suggestions.  I have the boot order set to Cd, floppy then hdd, and with the disk in the drive turn off and then turn on the computer, it boots to just past the first screen - displays COMPAQ, then within several seconds the 'missing operating system' message comes up with the cursor flashing.  I've tried it with a Windows Xp installation disk, the Ubuntu desktop and the Ubuntu server disk and the same message is displayed...(I downloaded the two Ubuntus at x2 speed) and I know the XP disk works.  Any further suggestions?!

---

### Post by Herman on 2006-11-17
Here's a link about your error message, [Missing operating system]("http://www.pcguide.com/ts/x/sys/booterrGBER44-c.html")

It's odd that your computer would boot up those bootable CDs before, but it won't now. I don't know, a hardware problem maybe? Clean the CD drive with a cleaning disk? Look again in the BIOS maybe, just to make sure?

---

